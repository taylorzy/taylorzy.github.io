---
layout: post
title: Binary tree traversal
---

<h2 class="lightBlue">{{ page.title }}</h2>

<p class="description">{{ page.date | date_to_string }}</p>

TreeNode Class:

{% highlight java linenos %}
public class TreeNode {
  private TreeNode right;
  private TreeNode left;
  private int val;
  public TreeNode(int val) {
    this.val = val;
  }
  public TreeNode leftNode() {
    return left;
  }
  public TreeNode rightNode() {
    return right;
  }
  public void setRight(TreeNode right) {
    this.right = right;
  }
  public void setLeft(TreeNode left) {
    this.left = left;
  }
  public void printNodeValue() {
    System.out.print(" " + val);
  }
}
{% endhighlight %}

Three Traversal Orders:

{% highlight java linenos %}
public class TraverseBinaryTree {
  public void preOrder(TreeNode root) {
    if (root == null)
      return;
    root.printNodeValue();
    preOrder(root.leftNode());
    preOrder(root.rightNode());
  }
  public void inOrder(TreeNode root) {
    if (root == null)
      return;
    inOrder(root.leftNode());
    root.printNodeValue();
    inOrder(root.rightNode());
  }
  public void postOrder (TreeNode root) {
    if(root == null) return;
    postOrder(root.leftNode());
    postOrder(root.rightNode());
    root.printNodeValue();
  }
}
{% endhighlight %}