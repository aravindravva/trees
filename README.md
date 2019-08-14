# trees
class node:
    def __init__(self,d):
        self.data=d
        self.left=None
        self.right=None
def insert(a,d):
        add=node(d)
        while(a):
            if(a.data<d):
                if(a.right==None):
                    #print("we are inserting to right of",a.data)
                    a.right=add
                    break
                else:
                    a=a.right
            else:
                if(a.left==None):
                    #print("we are inserting left of",a.data)
                    a.left=add
                    break
                else:
                    a=a.left
        add.data=d
        add.left=None
        add.right=None

def inorder(a):
    if(a):
        inorder(a.left)
        print(a.data)
        inorder(a.right)
def search(a,key):
    while(a):
        if(a.data==key):
            print('found')
            return a
        elif(a.data<key):
            a=a.right
        else:
            a=a.left
    print('not found')
def minimum(a):
    while(a):
        if(a.left==None):
            return a.data
        else:
            a=a.left
    return a.data
def maximum(a):
    while(a):
        if(a.right==None):
            return a.data
        else:
            a=a.right
    return a.data
def parent(a,root):
    while(root.left!=None and root.right!=None):
        if(root.left.data==a.data or  root.right.data==a.data):
            return root
        elif(root.left.data>a.data):
            root=root.left
        else:
            root=root.right 
def sucess(a,key):
    root=a
    a=search(a,key)
    val=a.data
    if(a.right):
        return minimum(a.right)
    else:
        p=parent(a,root)
        while(p!=None):
            if(p.data<a.data):
                p=parent(a,root)
            else:
                print(p.data)
                return p.data
        
           
l=list(map(int,input().split()))
a=node(l[0])
root=a
for i in l[1:]:
    insert(a,i)
#inorder(a)
key=int(input("enter element to find"))
#a=search(a,key)
print(sucess(root,key))
#print(minimum(root))
#print(maximum(root))
