# Iterator-and-Database
class FibonacciIterator:
    def __init__(self):
        self.prev = 0
        self.curr = 1

    def __iter__(self):
        return self

    def __next__(self):
        fib = self.prev
        self.prev, self.curr = self.curr, self.prev + self.curr
        return fib
    
# Python va Database
import psycopg2

conn = psycopg2.connect(
    dbname="db_manager",
    user="mirfayz13",
    password="Bukhara04",
    host="db_host",
    port=5432
)

cursor = conn.cursor()
def create_student(name, age):
    sql = "INSERT INTO students(name, age) VALUES (%s, %s)"
    cursor.execute(sql, (name, age))
    conn.commit()
    print("Done")

def delete_student(student_id):
    sql = "DELETE FROM students WHERE id = %s"
    cursor.execute(sql, (student_id,))
    conn.commit()
    print("Student deleted successfully.")

cursor.close()
conn.close()
