---
title: ptr::Release
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr.Release
- ptr::Release
- msclr.com.ptr.Release
- msclr::com::ptr::Release
helpviewer_keywords:
- Release method
ms.assetid: 7855781e-e4f6-4ad5-86a5-a81e2c3d90db
ms.openlocfilehash: 276d79688213864c31cf04a59f48a8799bf84371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544922"
---
# <a name="ptrrelease"></a>ptr::Release

Libère toutes les références détenues sur l’objet COM.

## <a name="syntax"></a>Syntaxe

```
void Release();
```

## <a name="remarks"></a>Notes

Appel de cette fonction libère détenus toutes les références sur l’objet COM et définit le handle interne vers l’objet COM à `nullptr`.  Si aucune autre référence sur l’objet COM n’existe, il sera détruit.

## <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son membre privé `IXMLDOMDocument` objet.  Le `ReplaceDocument` fonction membre utilise `Release` pour libérer de n’importe quel objet de document précédente avant d’attacher le nouveau document.

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

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Voir aussi

[ptr, membres](../dotnet/ptr-members.md)<br/>
[ptr::Detach](../dotnet/ptr-detach.md)