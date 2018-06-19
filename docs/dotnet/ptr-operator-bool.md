---
title: PTR::operator (bool) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr::operator bool
- ptr.operator bool
- operator bool
- msclr::com::ptr::operator bool
- msclr.com.ptr.operator bool
dev_langs:
- C++
helpviewer_keywords:
- ptr::operator bool
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 263810b4fbd369445c2ead55277381bc81b092d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161562"
---
# <a name="ptroperator-bool"></a>ptr::operator (bool)
Opérateur pour l’utilisation de `com::ptr` dans une expression conditionnelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator bool();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si l’objet COM détenue est valide ; `false` dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
 L’objet COM détenue est valide si elle n’est pas `nullptr`.  
  
 Cet opérateur convertit effectivement en `_detail_class::_safe_bool` qui est plus sûr que `bool` car il ne peut pas être converti en un type intégral.  
  
## <a name="example"></a>Exemple  
 Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son membre privé `IXMLDOMDocument` objet. Le `CreateInstance` fonction membre utilise `operator bool` après la création de l’objet document pour déterminer si elle est valide et qu’elle écrit dans la console s’il s’agit.  
  
```  
// comptr_op_bool.cpp  
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
         if (m_ptrDoc) { // uses operator bool  
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
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Voir aussi  
 [PTR, membres](../dotnet/ptr-members.md)   
 [ptr::operator!](../dotnet/ptr-operator-logical-not.md)