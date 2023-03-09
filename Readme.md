# Grid View for ASP.NET Web Forms - How to add a column if the AutoGenerateColumns property is set to true
<!-- run online -->
**[[Run Online]](https://codecentral.devexpress.com/e3587/)**
<!-- run online end -->
This example demonstrates how to add a column to the grid when the AutoGenerateColumns is enabled.

![addColumn](images/addColumn.png)

## Overview

When the [AutoGenerateColumns](https://docs.devexpress.com/AspNet/DevExpress.Web.ASPxGridView.AutoGenerateColumns) property is set to `true`, handle the [DataBound](https://docs.devexpress.com/AspNet/DevExpress.Web.ASPxDataWebControlBase.DataBound) event add a column to the [Grid View](https://docs.devexpress.com/AspNet/DevExpress.Web.ASPxGridView) control. Before you add a column, check whether this column already exists to avoid duplicate columns.

```aspx
<dx:ASPxGridView ID="ASPxGridView1" runat="server" AutoGenerateColumns="True" 
    KeyFieldName="CategoryID" ondatabound="ASPxGridView1_DataBound">
</dx:ASPxGridView>
```

```cs
protected void ASPxGridView1_DataBound(object sender, EventArgs e) {
    if (grid.Columns.IndexOf(grid.Columns["CommandColumn"]) != -1)
        return;
    GridViewCommandColumn col = new GridViewCommandColumn();
    col.Name = "CommandColumn";
    // ...
    grid.Columns.Add(col);
}
```

## Files to Review

* [Default.aspx](./CS/WebSite/Default.aspx) (VB: [Default.aspx](./VB/WebSite/Default.aspx))
* [Default.aspx.cs](./CS/WebSite/Default.aspx.cs) (VB: [Default.aspx.vb](./VB/WebSite/Default.aspx.vb))

## More Examples

* [Grid View for ASP.NET MVC - How to add a column if the AutoGenerateColumns property is set to true](https://github.com/DevExpress-Examples/mvc-gridview-add-column-to-autogenerated-columns)
