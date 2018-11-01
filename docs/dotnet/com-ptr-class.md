---
title: com::ptr, classe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- com::ptr
- msclr::com::ptr
- msclr.com.ptr
- com.ptr
helpviewer_keywords:
- ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: c4d5818698f553fe1d003aab6ca3c7f31e85f843
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665362"
---
# <a name="comptr-class"></a>com::ptr, classe

Wrapper pour un objet COM qui peut être utilisé en tant que membre d’une classe CLR.  Le wrapper automatise également la gestion de la durée de vie de l’objet COM à libérer détenus toutes les références sur l’objet lorsque son destructeur est appelé. Analogue à [classe CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntaxe

```
template<class _interface_type>
ref class ptr;
```

#### <a name="parameters"></a>Paramètres

*_interface_type*<br/>
Interface COM.

## <a name="remarks"></a>Notes

Un `com::ptr` peut également servir en tant que fonction locale variable afin de simplifier les diverses tâches de COM et d’automatiser la gestion de la durée de vie.

Un `com::ptr` ne peut pas être utilisé directement comme paramètre de fonction ; utilisez un [opérateur de référence de suivi](../windows/tracking-reference-operator-cpp-component-extensions.md) ou un [gérer sur l’opérateur Object (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) à la place.

Un `com::ptr` ne peut pas être retourné directement à partir d’une fonction ; utilisez un handle à la place.

## <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son membre privé `IXMLDOMDocument` objet.  Les méthodes publiques de la classe entraîne l’appel dans les appels à la relation contenant-contenu `IXMLDOMDocument` objet.  L’exemple crée une instance d’un document XML, il remplit avec du code XML simple et est un parcours simplifié des nœuds dans l’arborescence du document analysé pour imprimer le code XML dans la console.

```
// comptr.cpp
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
         // load some XML into the document
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

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
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
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Voir aussi

[Bibliothèque de prise en charge C++](../dotnet/cpp-support-library.md)<br/>
[ptr, membres](../dotnet/ptr-members.md)