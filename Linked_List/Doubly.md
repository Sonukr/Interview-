## What is Doubly Linked List
- A doubly linked list is a linked data structure that consists of a set of sequentially linked records called nodes. Each node contains two fields, called links, that are references to the previous and to the next node in the sequence of nodes.

- We will have all the methods as per singly linked list.

```js

function Node(value) {
  this.value = value;
  this.next = undefined;
  this.prev = undefined;
}

function DoublyLinkedList() {
  var head = undefined;
  var tail = undefined;
  var length = 0;

  return {
    insert: function(item) {
      if (!item) return;

      var node = new Node(item);

      if (head) {
        node.next = head;
	      head.prev = node;
      }

      head = node;
			
      if (!tail){
        tail = node;
      }
		
      length++;
    },

    delete: function(value) {
      var curr = head; //Start from head of the list

      //Iterate through list to find the matching node
      while (curr) {
        if (curr.value === value){
          var prev = curr.prev, next = curr.next;

          //Update the pointers
          if (prev){
            prev.next = next;
          }
          else{
            head = next; //If matched node is the head
          }

          if (next){
            next.prev = prev;
          }
          else{
            tail = prev;//If matched node is the tail
          }

          length--;
          break;
        }
        curr = curr.next;
      }
    },

    search: function(value) {
      var curr = head;
      var found = undefined;

      while (curr) {
        if (curr.value === value) {
          found = curr;
          break;
        }

        curr = curr.next;
      }

      return found;
    },

    getSize() {
      return length;
    },

    print: function() {
      var result = [];

      var curr = head;
      while (curr) {
        result.push(curr.value);

        curr = curr.next;
      }
      return result;
    }
  }
}

// Use

var LinkedList = new DoublyLinkedList();
console.log(LinkedList.insert(2))
console.log(LinkedList.search(2))
console.log(LinkedList.getSize())
console.log(LinkedList.delete(2))
console.log(LinkedList.getSize())

```