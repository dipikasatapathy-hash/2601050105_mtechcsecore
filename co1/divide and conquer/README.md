Divide-and-Conquer for Sorting 1 Crore Student Records
A suitable Divide-and-Conquer algorithm is Merge Sort.

Suppose we need to sort 1 crore (10 million) student records by student ID, name, or marks.

Divide:
Split the 1 crore records into two roughly equal parts:

Part 1 → 50 lakh records
Part 2 → 50 lakh records
Continue dividing each part until the sublists are small enough to be sorted easily.

Conquer:
Recursively sort each smaller sublist. When a sublist contains one record, it is already sorted.

Combine:
Merge the sorted sublists together while maintaining the required order. Continue merging until all 1 crore records form one completely sorted dataset.

Example
10 crore? No → 1 crore records
             ↓
        Divide into 2
       /             \
  50 lakh          50 lakh
    ↓                 ↓
  Divide            Divide
    ↓                 ↓
 Sort smaller      Sort smaller
    \                 /
       Merge
         ↓
   1 crore sorted records

Time complexity: O(n log n)
For n = 10,000,000, Merge Sort is efficient because each record participates in about log₂(n) levels of merging.

In short:
Divide: Split the dataset → Conquer: Sort each part recursively → Combine: Merge the sorted parts into one sorted dataset.

def merge_sort(students):
    # Divide
    if len(students) <= 1:
        return students

    mid = len(students) // 2

    left = merge_sort(students[:mid])
    right = merge_sort(students[mid:])

    # Combine
    return merge(left, right)


def merge(left, right):
    result = []
    i = 0
    j = 0

    # Combine two sorted lists
    while i < len(left) and j < len(right):
        if left[i]["marks"] <= right[j]["marks"]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    # Add remaining elements
    result.extend(left[i:])
    result.extend(right[j:])

    return result


# Example student records
students = How Divide-and-Conquer is applied
1. Divide:
The merge_sort() function divides the student records into two halves repeatedly.

mid = len(students) // 2
left = students[:mid]
right = students[mid:]

2. Conquer:
Each half is recursively sorted.

left = merge_sort(left)
right = merge_sort(right)

3. Combine:
The merge() function combines the two sorted halves into one sorted list.

return merge(left, right)

For 1 crore (10 million) records, the same algorithmic idea applies, with O(n log n) time complexity. In a real system, however, keeping all 10 million records and recursive slices in memory may be expensive; an external merge sort is often more appropriate when the dataset doesn't fit comfortably in RAM.




    {"name": "Rahul", "marks": 75},
    {"name": "Anu", "marks": 92},
    {"name": "Kiran", "marks": 68},
    {"name": "Priya", "marks": 85},
    {"name": "Ravi", "marks": 78}
]

sorted_students = merge_sort(students)

print("Sorted Students:")
for student in sorted_students:
    print(student)
