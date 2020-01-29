---
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
      values:
        layout: single
        categories: Translation
        author_profile: true
        read_time: true
        comments: true
        share: true
        related: true
---

### 1. Stack


### 2. Sets


### 3. Queue
  Similiar to stack but it has first in frist out sturcture like waiting line or priting queue so It can be implementing with JS array
- enqueue
   - Putting the item to the array(collection) this case item goes to the end  
    ```js
    queue.push(item);
    ```
- dequeue
   - returning the item which was stored at first 
   ```js
    return collection.shift();
    ```

- PriorityQueue
   - Not only pass the item to queue but also pass the priority of element and sorting the items depends on priority but if the priortiy is the same it eaxctly runs same as nomral queue
        ```js
        let queue = [];
        this.enqueue =(elment) =>{
            let added = false;
            foreach(let i in queue.length) {
            (element[1] < queue[i][1] ? queue.splice(i,0,element); //checking priority)
            break;
            added = ture
            } 
            (added ? queue.push(element) : null)  
        }
        ```

### 4. Binary Search Tree
- BST has always two branch in every `node` and certain order 
```js
  //Represent each node at the Tree which has 3 data props
  class Node{
      constructor (data , left=null, right=null){
          this.data = data;
          this.right = right;
          this.left = left;
      }
  }

    class BinarySearchTree {
      constructor() {
          this.node =null
      }
    }
```
- How to add the data to BST 
  1. get a referance from node if it is null set the data to root
  2. if it is not let's going to use a recursive function(`serchTree`)
  ```js
    add(data) {
        if(node === null) {
            this.root = new Node(data);
            return 
        } else {
        const searchTree = (node) =>{
        if(data < node.data) {
            if(node.left === null) {
                node.left = new Node(data);
                return;
            }else if(node.left !== null) {
                return searchTree(node.left);
            }
        } else if(data > node.data) {
            if(node.right === null) {
                node.right = new Node(data);
            } else if(node.right !== null) {
                return searchTree(node.right);
            }
        } else {
            return null;
            } 
        }
    return searchTree(node);
    }
    ```
- How to find a `MinValue` or `MaxValue`
    1. if it is the cas for seeking a min value it should go 
    findMin() {

    }
    findMax() {

    }
    isPresnt() {

    }

    remove(data) {
        
    }
    }
    ```