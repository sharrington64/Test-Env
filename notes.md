# Algorithms & Data Structures

### Big O Notation
1. Growth is with respect to the input- More values, the more the computation grows. N
2. Constants are dropped. - We don't care if o(n-2), it's just O(n)
3. Worst Case is the way we measure. Assume the result is at the end.

### Arrays
An array is continuous amount of memory space that contains a certain amount of bytes.

binary search = go to half, check. if not, half again previous or next based on value at half.

```

export default function bs_list(haystack: number[], needle: number): boolean {
        let lo = 0;
        let hi = haystack.length;
        do {
            const m = Math.floor(lo + (hi - lo)/2);
            const v = haystack[m];
            if(v === needle){
                return true;
            }
            else if (v > needle){
                hi = m;
            }
            else {
                lo = m +1;
            }
        } while (lo < hi);
        return false;
}

```
Bubble Sort = if this < that, cool. if not, swap this and that, continue.

```
export default function bubble_sort(arr: number[]): void {
    for(let i = 0; i < arr.length; i++){
        for(let j = 0; j < arr.length -1 -i; j++){
            if(arr[j] > arr[j+1]){
                const tmp = arr[j];
                arr[j] = arr[j + 1];
                arr[j+1] = tmp;
            }
        }
    }
}

```

### Linked List
a = [] is not an array. It is a Linked list. What is a linked list?
an element wrapped in a node with a link to next. Doubly linked list contains a link to previous and next. In order to modify the elements, you first modify the references ie, a -> b -> c add d before b = a.next =d, b.prev =d, d.prev = a, d.next = b. Same with deleting. If you just delete the element, you're fucked.

### Queue
Just a first-in first-out line. Queue has head and tail reference. allows for queue, deque, peek, etc.

```
type Node<T> = {
    value:T,
    next?: Node<T>,
}
export default class Queue<T> {
    public length: number;
    private head?: Node<T>;
    private tail?: Node<T>;

    

    constructor() {
        this.head = this.tail = undefined;
        this.length = 0;
    }

    enqueue(item: T): void {
        const node = {value: item} as Node<T>
        if(!this.tail){
           this.tail = this.head = node; 
        }

        this.tail.next = node;
        this.tail = node;
    

}
    deque(): T | undefined {
        if(!this.head) {
            return undefined;
        }
        
        this.length --;

        const head = this.head;
        this.head = this.head.next;
        head.next = undefined;

        if(this.length === 0) {
            this.tail = undefined;
        }

        return head.value;
}
    peek(): T | undefined {
        return this.head?.value;
}
}

```
