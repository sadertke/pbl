# 몽고db  맵리듀스
---

* 맵리듀스란 ?
  map과 reduce를 합친것으로 하둡에서는 네임노드의 job tracker가 각 데이터 노드의 task tracker 에게  분산해서 처리한다
  map 은 입력값의 key : value 구조를 원하는 로직에 맞게 맵핑을 처리하고 셔플을 진행하면서 새로 정의된 key : value 단위로  모아
  reduce에서 처리후 병합한다 yarn에서는 컨테이너가 중간에 reduce를 처리해 셔플을 과정의 네트워크 부하를 줄인다는 것도 알아두자
  
* 기본 예제 word counter 
  이  예제에서는 몽고db에 저장된 document( json 형식) 을 이용해서 입력된 단어들과 그 횟수를 새로운 collection으로 보낼것이다
  
  ```json
  [{ "text" : "this is a book"},
    { "text" : "this is a book"},
    { "text" : "this is a book"}]
  
  ```

  위를 데이터는 각 데이터 노드로분할 된후 map function 과 reduce function을 호출하고 결과를 네임노드로 보낸다
    * map_func
 
 ```javascript
  map_f = function()
  {
    var res = this.text.split(' ');
    for(var i in res)
    {
    key = {word : res[i]}
    value = {count : 1}
    emit(key,value);
    }
  
  }
  ```
    * reduce_func
     
  ```javascript
  reduce_f = function(key,values)
  {
    var = totalcount =0;
    for(var i in values){
      totalcount = totalcount+values[i].count;
    }
    return {count : totalcount}
  
  }
  
  ```
  
  ```mongodb
  
    db.text.mapReduce(map_f,reduce_f,"wordcount)
  ```
  
 ## 영화 배우 예제 
  ```json
  [{ "actor" : "richard gere","movies" :['chicago','runway brige']},
    { "actor" : "rovert downey jr","movies" :['iron man','iron man2','avengers']},
    ]
  
  ```

 
 
  ```javascript
  map_f = function()
  {
    for(var i in this.movies)
    {
    key = {movie : this.movies[i]}
    value = {actor : this.actor}
    emit(key,value);
    }
  
  }
  ```
    * reduce_func
    
  ```javascript
  reduce_f = function(key,values)
  {
    actor_list = {actors:[]};
    for(var i in values){
      actor_list.actors = values[i].actor.concat(actor_list.actors);
    }
    return actor_list;
  
  }
  
  ```

  
  
  
  
