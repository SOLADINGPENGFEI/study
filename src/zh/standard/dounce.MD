# 防抖与节流
## 防抖的原理
- 触发事件的n时间后才执行，如果n时间内事件再次被触发，则以新触发的时间为标准，然后n时间后在执行
        export function Debounce(func, ms=500) {
            let timer = 0;

            return function() {
                window.clearTimeout(timer)
                timer = setTimeout(() => {
                    func()
                },ms)
            }
        }
## 节流的原理
- 在持续触发事件时候，每隔一段时间执行一次。我们可以使用time line或者定时器来实现，或者二者结合实现
        export function Throttle(func, ms=500) {
            let start = +new Date()

            return function() {
                let current = +new Date()
                if(current - start > ms) {
                    func()
                    start = current
                }
            }
        }
## 快速入口
[防抖与节流](https://www.jianshu.com/p/c8b86b09daf0)