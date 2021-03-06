---
title: "How to: Programmatically Save Documents | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documents [Office development in Visual Studio], saving"
  - "Word [Office development in Visual Studio], saving documents"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Programmatically Save Documents
  There are several ways to save Microsoft Office Word documents. You can save a document without changing the name of the document, or you can save a document with a new name.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Saving a Document Without Changing the Name  
  
#### To save the document associated with a document-level customization  
  
1.  Call the <xref:Microsoft.Office.Tools.Word.Document.Save%2A> method of the <xref:Microsoft.Office.Tools.Word.Document> class. To use this code example, run it from the `ThisDocument` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-cs[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### To save the active document  
  
1.  Call the <xref:Microsoft.Office.Interop.Word._Document.Save%2A> method for the active document. To use this code example, run it from the `ThisDocument` or `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-cs[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 If you are not sure whether the document you want to save is the active document, you can refer to it by its name.  
  
#### To save a document specified by name  
  
1.  Use the document name as an argument to the <xref:Microsoft.Office.Interop.Word.Documents> collection. To use this code example, run it from the `ThisDocument` or `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-cs[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## Saving a Document With a New Name  
 Use the SaveAs method to save a document with a new name. You can use this method of the <xref:Microsoft.Office.Tools.Word.Document> host item in a document-level Word project, or of a native <xref:Microsoft.Office.Interop.Word.Document> object in any Word project. This method requires that you specify the new file name, but other arguments are optional.  
  
> [!NOTE]  
>  If you show the **SaveAs** dialog box inside of the <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> event handler of `ThisDocument` and set the *Cancel* parameter to **false**, the application might quit unexpectedly. If you set the *Cancel* parameter to **true**, an error message appears indicating that Autosave has been disabled.  
  
#### To save the document associated with a document-level customization with a new name  
  
1.  Call the <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> method of the `ThisDocument` class in your project, using a fully qualified path and file name. If a file by that name already exists in that folder, it is silently overwritten. To use this code example, run it from the `ThisDocument` class.  
  
    > [!NOTE]  
    >  The <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> method throws an exception if a target directory does not exist or if there are other problems saving a file. It is a good practice to use a **try...catch** block around the <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> method or inside a calling method.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-cs[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### To save a native document with a new name  
  
1.  Call the <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> method of the <xref:Microsoft.Office.Interop.Word.Document> that you want to save, using a fully qualified path and file name. If a file by that name already exists in that folder, it is silently overwritten.  
  
     The following code example saves the active document with a new name. To use this code example, run it from the `ThisDocument` or `ThisAddIn` class in your project.  
  
    > [!NOTE]  
    >  The <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> method throws an exception if a target directory does not exist or if there are other problems saving a file. It is a good practice to use a **try...catch** block around the <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> method or inside a calling method.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-cs[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## Compiling the Code  
 This code example requires the following:  
  
-   To save a document by name, a document named NewDocument.doc must exist in a directory named Test on drive C.  
  
-   To save a document with a new name, a directory named Test must exist on drive C.  
  
## See Also  
 [How to: Programmatically Close Documents](../vsto/how-to-programmatically-close-documents.md)   
 [How to: Programmatically Open Existing Documents](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Document Host Item](../vsto/document-host-item.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  