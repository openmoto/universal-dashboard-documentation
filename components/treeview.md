# Tree View

Required Version: 2.0.0

![](..\updates\images\2.0.0\treeview.gif)

The tree view control is used to display and navigate container based data. You can use the `New-UDTreeView` and `New-UDTreeNode` to create a tree view. Data can be loaded dynamically and clicking on nodes can invoke an Endpoint.

## Creating a basic tree view 

To create a basic tree view, you can first create a new tree view control via `New-UDTreeView` and add nodes to it via `New-UDTreeNode`. You can nest nodes within each other. 

```powershell
New-UDTreeView -Node (
    New-UDTreeNode -Name "Root Node" -Children {
        New-UDTreeNode -Name "Child 1" 
        New-UDTreeNode -Name "Child 2" 
        New-UDTreeNode -Name "Child 3" -Children {
            New-UDTreeNode -Name "Child Child 1
        } 
    }
)
```

## Creating a dynamic tree view

To create a dynamic tree view, you can use the `-OnNodeClicked` ScriptBlock to return nodes dynamically when the node is clicked. 

The body variable passed into the `-OnNodeClicked` ScriptBlock is the node that was clicked. After converting from JSON you can look at the `NodeId` property to create child nodes. 

In the below example, the depth of the node is set as the ID and incremented when clicking the node.

```powershell
 $Root = New-UDTreeNode -Name '1' -Id '1'
New-UDTreeView -ActiveBackgroundColor '#DFE8E4' -Node $Root -OnNodeClicked {
    param($Body)

    $Obj = $Body | ConvertFrom-Json
    $Depth = ([int]$Obj.NodeId) + 1

    New-UDTreeNode -Name ($Depth).ToString() -Id  ($Depth).ToString()
} 
```
