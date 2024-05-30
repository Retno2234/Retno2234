
class Node:
    def __init__(self, data):
        self.data = data 
        self.next = None 

class Queue:
    def __init__(self):
        self.front = None
        self.rear = None

    def is_empty(self):
        return self.front is None

    def enqueue(self, data):
        new_node = Node(data)
        if self.rear is None:
            self.front = self.rear = new_node
            return
        self.rear.next = new_node
        self.rear = new_node

    def dequeue(self):
        if self.is_empty():
            print("Antrian kosong, tidak ada yang dapat dihapus")
            return None
        temp = self.front
        self.front = temp.next
        if self.front is None:
            self.rear = None
        return temp.data

    def display(self):
        if self.is_empty():
            print("Antrian kosong")
            return
        current = self.front 
        while current:
            print(current.data, end=" -> ")    
            current = current.next
        print("None")

# Menampilkan penggunaan
queue = Queue()
queue.enqueue("Nasabah 1")
queue.enqueue("Nasabah 2")
queue.enqueue("Nasabah 3")

print("Antrian setelah beberapa nasabah mengantri:")
queue.display()

print("\nNasabah yang dilayani dan keluar dari antrian:")
print(queue.dequeue())

print("\nAntrian setelah melayani satu nasabah:")
queue.display()
