---
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
      values:
        layout: single
        categories: Data Structure
        author_profile: true
        read_time: true
        comments: true
        share: true
        related: true
---

The Basic Data Structure in JavaScript (`Stack` , `Set` , `Queue` , `Binary Search Tree`)

### 1. Stack
This sturcture is smiliar with a brower history like if there is a site user visited it goes to stack up to the histroy and you can pop up(go back) to the most recent site you visited. It can be implemented by using container like array

- push
  - putting the item to the array to the end
  ```js
  stack.push(items);
  ```
- pop
  - Getting the data which is most recent and delete the item in the stack
  ```js
  stack.pop(item);
  ```
- size(length)
  - getting the size of stack
  ```js
  stack.length;
  ```
- peek
  - Just return the lastes item and dont delete the item in the stack;
    ```js
    return stack[stack.legth-1]; 
    // or
    return stack.splice(-1);
    ```

### 2. Sets
This is smilair with array stucture but there is no duplicate item in it as well as there is no paricular order so simply using that checking the items

- add
  - Appends the given value to the `Set` as long as the given value is new element 
  ```js
  Set.add(value);
  ```
- clear & delete
    - if you want to remove all the element use clear and want to remove the item which is in the set use the delete method if it the given value doest exist in the set it will return `false`
    ```js
    Set.clear();
    Set.remove(value);
    ```
- has
  - if you want to check whether the given value is present in set it will return the boolean
 ```js
 Set.has(value);
 ```

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
 BST has tree stucture and two branches in every `node` and certain order 
- basic structure of Binary search Tree.
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
 - if it is the case for seeking a min value you should go all the way to the left unless the node is null 
   ```js
    findMin() {
        let current= this.root;
        while(current.left !== null) {
            current  = current.left;
        }
        return current.data;
    }
    ```
    - the case for seeking the max value you can just go all the way to the right unless the node is null
    ```js
    findMax() {
        let current= this.root;
        while(current.right !== null) {
            current = current.right;
        } 
        return current.data;
    }
    ```
- Checking the value if it is in the current BST
  ```js
    isPresnt(data) {
        let current  = this.root;
        while(current) {
            if(data === current.data) {
                return true;
            }
            if(data < current.data) {
                current = current.left;
            } else {
                current = current.right;
            } 
        }
        return false;
    }
  ```
 - Remove the data using recursive function
   - Checking the node whether it is null or not
   - Checking the node whether it equals as data which wants to remove then remoivng the data depends on the case of existence of children
     - 1) if the node has no children : making sure their left and right node is empty then return null
     - 2) if the node only has one child return their child (you can just replace it!)
     - 3) if the node has both children you should replace the most closest one which is loacted all the way down left from the right children of data using recursive function
   - if the data is either smaller or bigger than node keep searching the data using recursive function so if the case of bigger than node you should call the fucntion to right side of node if it is opposite case do the same thing to the left side. 
    ```js  
    remove(data) {
        const removeNode = (node , data) => {
            if(node == null) {
                return null;
            }
            if(data == node.data) {
                //Has no children
                if(node.left == null && node.right == null) {
                    return null;
                }

                //Has only one child
                if(node.left == null) {
                    return node.right;
                }
                if(node.right == null) {
                    return node.left;
                }

                //Has both children
                let tempNode =node.right;
                while(tempNode.left !== null) {
                    tempNode = tempNode.left;
                }
                node.data = tempNode.data;
                node.right = removeNode(node.right, tempNode.data);
                return node;
            } else if(data < node.data) {
                node.left = removeNode(node.left , data);
                return node;
            } else {
                node.right = removeNode(node.right, data);
                return node;
            }
         }
         this.root = removeNode(this.root , data);
        }
    }
    ```