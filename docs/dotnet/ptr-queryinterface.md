---
title: "ptr::QueryInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ptr.QueryInterface"
  - "ptr::QueryInterface"
  - "msclr::com::ptr::QueryInterface"
  - "msclr.com.ptr.QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QueryInterface (méthode)"
ms.assetid: c2619517-3fde-493b-b12d-da8f62d5d803
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ptr::QueryInterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Interroge l'objet COM propriétaire pour une interface et joint le résultat à un autre `com::ptr`.  
  
## Syntaxe  
  
```  
template<class _other_type>  
void QueryInterface(  
   ptr<_other_type> % other  
);  
```  
  
#### Paramètres  
 `other`  
 Le `com::ptr` qui obtiendra l'interface.  
  
## Exceptions  
 En interne, `QueryInterface` est appelé sur l'objet COM possédé et toute erreur `HRESULT` est convertie en une exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.  
  
## Notes  
 Utilisez cette méthode pour créer un wrapper COM pour une interface différente de l'objet COM appartenant au wrapper actuel.  Cette méthode appelle `QueryInterface` via l'objet COM propriétaire pour demander un pointeur vers une interface spécifique de l'objet COM et attache le pointeur d'interface retourné au `com::ptr`.  
  
## Exemple  
 Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son objet membre privé `IXMLDOMDocument`.  La fonction membre `WriteTopLevelNode` utilise `QueryInterface` pour remplir localement `com::ptr` avec `IXMLDOMNode` puis passer `com::ptr` \(par suivi des références\) dans une fonction membre privée qui écrit le nom et les propriétés du texte de nœud dans la console.  
  
```  
// comptr_queryinterface.cpp  
// compile with: /clr /link msxml2.lib  
#include <msxml2.h>  
#include <msclr\com\ptr.h>  
  
#import <msxml3.dll> raw_interfaces_only  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
using namespace msclr;  
  
// a ref class that uses a com::ptr to contain an   
// IXMLDOMDocument object  
ref class XmlDocument {  
public:  
   // construct the internal com::ptr with a null interface  
   // and use CreateInstance to fill it  
   XmlDocument(String^ progid) {  
      m_ptrDoc.CreateInstance(progid);     
   }  
  
   void LoadXml(String^ xml) {  
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);  
      BSTR bstr = NULL;  
  
      try {  
         // load some XML into our document  
         bstr = ::SysAllocString(pinnedXml);  
         if (NULL == bstr) {  
            throw gcnew OutOfMemoryException;  
         }  
         VARIANT_BOOL bIsSuccessful = false;  
         // use operator -> to call IXMODOMDocument member function  
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));  
      }  
      finally {  
         ::SysFreeString(bstr);  
      }  
   }  
  
   // write the top level node to the console  
   void WriteTopLevelNode() {  
      com::ptr<IXMLDOMNode> ptrNode;  
  
      // query for the top level node interface  
      m_ptrDoc.QueryInterface(ptrNode);  
      WriteNode(ptrNode);  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   // simplified function that only writes the node  
   void WriteNode(com::ptr<IXMLDOMNode> % node) {  
      BSTR bstr = NULL;  
  
      try {  
         // write out the name and text properties  
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));  
         String^ strName = gcnew String(bstr);  
         Console::Write("<{0}>", strName);  
         ::SysFreeString(bstr);  
         bstr = NULL;  
  
         Marshal::ThrowExceptionForHR(node->get_text(&bstr));  
         Console::Write(gcnew String(bstr));  
         ::SysFreeString(bstr);  
         bstr = NULL;  
  
         Console::WriteLine("</{0}>", strName);  
      }  
      finally {  
         ::SysFreeString(bstr);  
      }  
   }  
  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      // stream some xml into the document  
      doc.LoadXml("<word>persnickety</word>");  
  
      // write the document to the console  
      doc.WriteTopLevelNode();  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
  **\<\#document\>persnickety\<\/\#document\>**   
## Configuration requise  
 **Fichier d'en\-tête** \<msclr\\com\\ptr.h\>  
  
 **Espace de nommage** msclr::com  
  
## Voir aussi  
 [ptr, membres](../dotnet/ptr-members.md)   
 [ptr::GetInterface](../dotnet/ptr-getinterface.md)