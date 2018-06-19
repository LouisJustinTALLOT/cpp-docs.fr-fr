---
title: PTR::Release | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.Release
- ptr::Release
- msclr.com.ptr.Release
- msclr::com::ptr::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 7855781e-e4f6-4ad5-86a5-a81e2c3d90db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6967567d8853a38c93e046093c37252eb904e8d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160587"
---
# <a name="ptrrelease"></a>ptr::Release
Libère toutes les références appartenant à l’objet COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Release();  
```  
  
## <a name="remarks"></a>Notes  
 Appel de cette fonction libère détenus toutes les références à l’objet COM et définit le handle interne vers l’objet COM `nullptr`.  Si aucune autre référence sur l’objet COM n’existe, il sera détruit.  
  
## <a name="example"></a>Exemple  
 Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son membre privé `IXMLDOMDocument` objet.  Le `ReplaceDocument` fonction membre utilise `Release` pour libérer un objet de document précédente avant de joindre le nouveau document.  
  
```  
// comptr_release.cpp  
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
  
   // replace currently held COM object with another one  
   void ReplaceDocument(IXMLDOMDocument* pDoc) {  
      // release current document object  
      m_ptrDoc.Release();  
      // attach the new document object  
      m_ptrDoc.Attach(pDoc);  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// unmanaged function that creates a raw XML DOM Document object  
IXMLDOMDocument* CreateDocument() {  
   IXMLDOMDocument* pDoc = NULL;  
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,  
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));  
   return pDoc;  
}  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      // get another document object from unmanaged function and  
      // store it in place of the one held by our ref class  
      pDoc = CreateDocument();  
      doc.ReplaceDocument(pDoc);  
      // no further need for raw object reference  
      pDoc->Release();  
      pDoc = NULL;  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
   finally {  
      if (NULL != pDoc) {  
         pDoc->Release();  
      }  
   }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Voir aussi  
 [PTR, membres](../dotnet/ptr-members.md)   
 [ptr::Detach](../dotnet/ptr-detach.md)