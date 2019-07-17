## What is Linked List
- Linked List is the structure where all elements are arranged in linear order, which is determined by pointer stored in each element.

-  Singly Linked list is the simplest linked structure. Each of the element will 

- We are going to implemwent following operations
    - **Insert** — here for the sake of convenience and maintain constant running time (O(1)), we will always insert new node to the beginning of the list.

    - **Delete**  — this method receive a parameter — the item data to delete.

    - **Search** — can be done iteratively or recursively. Here we will do it interative way but checking from the head of list until we found/the end, or checking from the end of the list (up to your choice for doubly list).

    - **Print** - This will return current Linked List.
    
    - **GetSize**- This is for getting current size of linked List


```js
function Node(value) {
  this.value = value;
  this.next = undefined;
}

function SinglyLinkedList() {
  var head = undefined;
  var length = 0;

  return {
    insert: function(item) {
      if (!item) return;

      var node = new Node(item);

      if (head) {
        node.next = head;
      }

      head = node;
      length++;
    },

    delete: function(value) {
      var curr = head;

      if (head.value === value) {
        head = head.next;
		    length--;
        return;
      }

      while (curr) {
        if (curr.next) {
          var next = curr.next;

          if (next.value === value) {
            curr.next = next.next;
            length--;
            break;
          }
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

var LinkedList = new SinglyLinkedList();
console.log(demoLinkedList.insert(2))
console.log(demoLinkedList.getSize())
console.log(demoLinkedList.delete(2))
console.log(demoLinkedList.getSize())

```

Looking for [Doubly Linked List](https://github.com/Sonukr/interview/blob/master/Linked_List/Doubly.md) ?