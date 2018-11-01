---
title: ptr::operator!
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr::operator!
- msclr::com::ptr::operator!
- ptr.operator!
- msclr.com.ptr.operator!
helpviewer_keywords:
- ptr::operator!
ms.assetid: 7f4101dc-2045-42e7-abb1-6a30e17147f2
ms.openlocfilehash: 8527afe20bf0b0896f2bd433b3dd3e4e8057357b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580893"
---
# <a name="ptroperator"></a>ptr::operator!

Opérateur afin de déterminer si l’objet COM détenu n’est pas valide.

## <a name="syntax"></a>Syntaxe

```
bool operator!();
```

## <a name="return-value"></a>Valeur de retour

**true** si l’objet COM détenu n’est pas valide ; **false** dans le cas contraire.

## <a name="remarks"></a>Notes

L’objet COM détenu est valide si elle n’est pas **nullptr**.

## <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son membre privé `IXMLDOMDocument` objet.  Le `CreateInstance` fonction membre utilise `operator!` pour déterminer si un objet de document est déjà détenu et crée uniquement une nouvelle instance si l’objet n’est pas valide.

```cpp
// comptr_op_not.cpp
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
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Voir aussi

[ptr, membres](../dotnet/ptr-members.md)<br/>
[ptr::operator bool](../dotnet/ptr-operator-bool.md)