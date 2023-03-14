# DataStructure-Merge-Sort


def merge_sort(list):
    if len(list) == 1:
        return list 
    
    left_half, right_half = split(list)
    left = merge_sort(left_half)
    right =merge_sort(right_half)
    
    return merge(left, right)

def split(list):
    mid = len(list) // 2
    left = list[:mid]
    right = list[mid:]
    return left, right 

def merge(left, right):
    l = []
    i = 0 
    j = 0 
    
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            l.append(left[i])
            i += 1 
        else:
            l.append(right[j])
            j += 1 
            
    while i < len(left):
        l.append(left[i])
        i += 1
        
    while j < len(right):
        l.append(right[j])
        j += 1 
        
    return l


def verify_sorted(list):
    n = len(list)
    if n == 0 or n == 1:
        return True
    
    #return  list[0] < list[1] and verify_sorted(list[1:]) 
    
    # or 
    
    # check if the first two elements of the list are in sorted order
    first_two_sorted = list[0] < list[1]

    # recursively check the remaining elements of the list
    rest_sorted = verify_sorted(list[1:])

    # return True only if both checks are True
    return first_two_sorted and rest_sorted


        
            
alist = [54, 62,1000, 9993, 93, 17, 77, 31, 44, 55, 20 ]
l = merge_sort(alist)
print(verify_sorted(alist))
print(verify_sorted(l))
       
            
            
