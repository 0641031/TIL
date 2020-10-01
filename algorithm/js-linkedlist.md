## Javascript - Linked List

```
class LinkedList {
  constructor(value){
    this.head = {
      value : value,
      next : null
    };
    this.tail = this.head;
    this.length = 1;
  }

  append(value) {
    const newNode = {
      value : value,
      next : null
    }
    this.tail.next = newNode;
    this.tail = newNode;
    this.length++;
  }

  prepend(value) {
    const newNode = {
      value : value,
      next : null
    }
    newNode.next = this.head;
    this.head = newNode;
    this.length++;
  }

  insert(index, value) {
    if(index >= this.length) {
      this.prepend(value);
    }

    const newNode = {
      value : value,
      next : null
    }

    let counter = 0;
    let currentNode = this.head;
    while(counter !== index-1) {
      currentNode = currentNode.next;
      counter++;
    }
    
    let temp = currentNode.next;
    currentNode.next = newNode;
    newNode.next = temp;
    this.length++;
  }

}
```


