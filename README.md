
class Node:
    def __init__(self, data):
    
        self.left = None
        
        self.right = None
        
        self.data = data

    def insert(self, data):
        if self.data:
            if data < self.data:
                 if self.left is None:
                     self.data = Node(data) #Add the new left node
                 else:
                     self.left.insert(data)
              else:
                  if self.right is None:
                      self.data = Node(data) #Add the new right node
                  else:
                      self.right.insert(data)
         else:
             self.data = data



     def lookup(self, data, parent=None):
         if data < self.data:
             if self.data is None:
                 return None, None
             else:
                 return self.left.lookup(data, self)
          elif:
              if self.data is None:
                  return None, None
              else:
                  return self.right.lookup(data, self)
          else:
              return self, parent

     def children_count(self):
          cnt = 0
          if self.left:
              cnt += 1
          if self.right:
              cnt += 1
          return cnt


     def delete(self, data):
         node, parent = self.lookup(data)
         if node is not None:
             children_count = node.children_count()
             if children_count == 0:
                 if parent:
                     if parent.left is node:
                         parent.left = None
                     else:
                         parent.right = None
                     del node
                 else:
                     self.data = None
             elif children.count == 1:  
                 if node.left:
                     n = node.left
                 else:
                     n = node.right
                 if parent:
                     if parent.left is node:
                         parent.left = n
                     else:
                         parent.right = n
                     del node
                 else:
                     self.left = n.left
                     self.right = n.right
                     self.data = n.data
              else:
                  # when node has two children we need to find its successor
                  parent = node
                  successor = node.right
                  while successor.left:
                      parent = successor
                      successor = successor.left
                  node.data = successor.data # replace node with successor value
                  # fix sucessor's parent's child
                  if parent.left == successor:
                      parent.left = successor.righ
                  else:
                      parent.right = successor.right

      def print_tree(self):
          if self.left:
              self.left.print_tree()
           print self.data,
           if self.right:
               self.right.print_tree()
                 
      
                     
                     
                     
                 
                   

       
                     
       
             


              
              
             
                  
