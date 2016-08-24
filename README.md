# MDSStorage
Storage插件
```
/**
 * Created by Redd on 2016/8/23.
 */
var MDSStorage = (function(){
    return {
        getSessionItem:function(key){
            if(window.sessionStorage){
                return sessionStorage.getItem(key);
            }else{
                try{
                   return JSON.parse(window.document.cookie)[key];
                }
                catch (ex){
                    console.log(ex);
                    return null;
                }
            }

        },
        setSessionItem:function(key,value){
            if(window.sessionStorage){
                sessionStorage.setItem(key,value);
            }else{
                try{
                    var data = JSON.parse(window.document.cookie||'{}');
                    data[key] = value;
                    window.document.cookie = JSON.stringify(data);
                }
                catch (ex){
                    console.log(ex);
                    return null;
                }
            }
        }
    }
})();
```
