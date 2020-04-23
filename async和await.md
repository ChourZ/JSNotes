之前在工作中遇到需要遍历list请求接口并且按顺序回调的问题，因为水平有限只能要求后台直接接受list。
今天又遇到一样的问题，找到了新的解决方法。
async和await一起使用可以解决这个问题，以下是我试错过程和解决方案。

1.在forEach中使用async和await

  
      list.forEach(async ele=>{
        await doSomething();
      })
返回会发现并不按照预想的顺序，仍然是随机返回，说明forEach不支持async和await。

2.在for循环中使用async和await

    const forTest=async _=>{
      for(let index=0;index<list.length;index++){
        await doSomething();
      }
    }
发现可以按顺序返回，达到要求。
