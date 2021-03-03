# Web Workers

Web workers are used to run code on different threads than the one our JS event loop is running in. It affects the single-threaded nature of Javascript to leverage multiple threads to run expensive **asynchronous** calculations.

Here's an example of a web worker:

```html
<!-- index.html -->
<script src="main.js"></script>
```
```javascript
// main.js
const worker = new Worker('worker.js')
worker.postMessage('Hello Worker')
worker.onmessage = e => {
  console.log('main.js: Message received from worker:', e.data)
}
// if you want to "uninstall" the web worker then use:
// worker.terminate()
```
```javascript
// worker.js
this.onmessage = e => {
  console.log('worker.js: Message received from main script', e.data)
  this.postMessage('Hello main')
}
```

A common library used to leverage this pattern is [https://github.com/developit/workerize]

Here's an example on how to use it:
```javascript
import makeFilterCitiesWorker from 'workerize!./filter-cities'
const {getItems} = makeFilterCitiesWorker()
export {getItems}
```