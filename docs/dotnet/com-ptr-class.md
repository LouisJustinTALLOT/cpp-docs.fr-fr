---
title: com::ptr, classe
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: e494285f33cf282d7b7515aac374ec86ef3036b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372492"
---
# <a name="comptr-class"></a>com::ptr, classe

Un emballage pour un objet COM qui peut être utilisé comme membre d’une classe CLR.  L’emballage automatise également la gestion à vie de l’objet COM, libérant toutes les références possédées sur l’objet lorsque son destructeur est appelé. Analogue à la [classe CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntaxe

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Paramètres

*_interface_type*<br/>
Interface COM.

## <a name="remarks"></a>Notes

A `com::ptr` peut également être utilisé comme variable de fonction locale pour simplifier diverses tâches COM et automatiser la gestion à vie.

A `com::ptr` ne peut pas être utilisé directement comme paramètre de fonction; utiliser un [opérateur de référence Tracking](../extensions/tracking-reference-operator-cpp-component-extensions.md) ou une poignée pour [l’opérateur d’objets (MD) à](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) la place.

A `com::ptr` ne peut pas être directement renvoyé d’une fonction; utiliser une poignée à la place.

## <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé.  Appeler les méthodes publiques de la classe `IXMLDOMDocument` entraîne des appels vers l’objet contenu.  L’échantillon crée une instance d’un document XML, le remplit avec un XML simple, et fait une promenade simplifiée des nœuds dans l’arbre de document analysé pour imprimer le XML à la console.

```cpp
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

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|---------|-----------|
|[ptr::ptr](#ptr)|Construit un `com::ptr` pour envelopper un objet COM.|
|[ptr::~ptr](#tilde-ptr)|Destructs `com::ptr`a .|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|---------|-----------|
|[ptr::Attach](#attach)|Attache un objet COM `com::ptr`à un .|
|[ptr::CreateInstance](#createInstance)|Crée une instance d’un `com::ptr`objet COM dans un .|
|[ptr::Detach](#detach)|Renonce à la propriété de l’objet COM, en retournant un pointeur à l’objet.|
|[ptr::GetInterface](#getInterface)|Crée une instance d’un `com::ptr`objet COM dans un .|
|[ptr::QueryInterface](#queryInterface)|Interroge l’objet COM possédé pour une interface `com::ptr`et attache le résultat à un autre .|
|[ptr::Release](#release)|Communiqués toutes les références possédées sur l’objet COM.|

### <a name="public-operators"></a>Opérateurs publics

|Nom|Description|
|---------|-----------|
|[ptr::opérateur-&gt;](#operator-arrow)|Opérateur d’accès membre, utilisé pour appeler les méthodes sur l’objet COM appartenant.|
|[ptr::opérateur](#operator-assign)|Attache un objet COM `com::ptr`à un .|
|[ptr::opérateur&nbsp;bool](#operator-bool)|Opérateur pour `com::ptr` l’utilisation dans une expression conditionnelle.|
|[ptr::operator!](#operator-logical-not)|opérateur pour déterminer si l’objet COM possédé est invalide.|

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<msclr-com-ptr.h>

**Namespace** msclr::com

## <a name="ptrptr"></a><a name="ptr"></a>ptr::ptr

Retourne un pointeur sur l’objet COM possédé.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur d'interface COM.

### <a name="remarks"></a>Notes

Le constructeur sans argumentation `nullptr` attribue à la poignée d’objet sous-jacente. Les appels `com::ptr` futurs vers l’objet valideront l’objet interne et échouent silencieusement jusqu’à ce qu’un objet soit créé ou joint.

Le constructeur d’un seul argument ajoute une référence à l’objet COM, mais ne `Release` libère pas la référence de l’appelant, de sorte que l’appelant doit faire appel à l’objet COM pour vraiment renoncer au contrôle. Lorsque `com::ptr`le déstructeur est appelé, il publiera automatiquement ses références sur l’objet COM.

Passer `NULL` à ce constructeur est la même chose que d’appeler la version sans argument.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé. Il démontre l’utilisation des deux versions du constructeur.

```cpp
// comptr_ptr.cpp
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

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>ptr: :ptr

Destructs `com::ptr`a .

```cpp
~ptr();
```

### <a name="remarks"></a>Notes

Sur la `com::ptr` destruction, les communiqués toutes les références qu’il possède à son objet COM. En supposant qu’il n’y ait pas d’autres références détenues à l’objet COM, l’objet COM sera supprimé et sa mémoire libérée.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé.  Dans `main` la fonction, `XmlDocument` les destructeurs des deux objets seront appelés lorsqu’ils sortiront de la portée du `try` bloc, ce qui entraînera l’appel du destructeur sous-jacent, `com::ptr` libérant toutes les références possédées à l’objet COM.

```cpp
// comptr_dtor.cpp
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

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
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

## <a name="ptrattach"></a><a name="attach"></a>ptr::Attach

Attache un objet COM `com::ptr`à un .

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Paramètres

*_right*<br/>
Le pointeur d’interface COM à attacher.

### <a name="exceptions"></a>Exceptions

Si `com::ptr` le possède déjà une référence `Attach` à <xref:System.InvalidOperationException>un objet COM, jette .

### <a name="remarks"></a>Notes

Un appel `Attach` à des références à l’objet COM mais ne libère pas la référence de l’appelant à celui-ci.

Passer `NULL` `Attach` aux résultats n’a pas été pris.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé. La `ReplaceDocument` fonction membre `Release` fait d’abord appel `Attach` à tout objet précédemment possédé, puis appelle à joindre un nouvel objet de document.

```cpp
// comptr_attach.cpp
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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>ptr::CréerInstance

Crée une instance d’un `com::ptr`objet COM dans un .

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>Paramètres

*Progid*<br/>
Chaîne `ProgID`.

*pouter*<br/>
Pointeur sur l’interface IUnknown de l’objet agrégé (le contrôle IUnknown). Si `pouter` n’est `NULL` pas spécifié, est utilisé.

*cls_context*<br/>
Contexte dans lequel le code qui gère l’objet nouvellement créé s’exécutera. Les valeurs sont `CLSCTX` tirées de l’énumération. Si `cls_context` elle n’est pas spécifiée, la valeur CLSCTX_ALL est utilisée.

*rclsid*<br/>
`CLSID`associés aux données et au code qui seront utilisés pour créer l’objet.

### <a name="exceptions"></a>Exceptions

Si `com::ptr` le possède déjà une référence `CreateInstance` à <xref:System.InvalidOperationException>un objet COM, jette .

Cette fonction `CoCreateInstance` appelle <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> et utilise `HRESULT` pour convertir toute erreur en une exception appropriée.

### <a name="remarks"></a>Notes

`CreateInstance`utilise `CoCreateInstance` pour créer une nouvelle instance de l’objet spécifié, identifié soit à partir d’un ProgID ou d’un CLSID. Les `com::ptr` références de l’objet nouvellement créé et libérera automatiquement toutes les références possédées lors de la destruction.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé. Les constructeurs de classe `CreateInstance` utilisent deux formes différentes de créer l’objet de document soit à partir d’un ProgID ou d’un CLSID plus un CLSCTX.

```cpp
// comptr_createinstance.cpp
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
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="ptrdetach"></a><a name="detach"></a>ptr::Detach

Renonce à la propriété de l’objet COM, en retournant un pointeur à l’objet.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Valeur retournée

Le pointeur de l’objet COM.

Si aucun objet n’est possédé, NULL est retourné.

### <a name="exceptions"></a>Exceptions

En `QueryInterface` interne, est appelé sur l’objet COM possédé et toute erreur `HRESULT` est convertie en une exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Notes

`Detach`ajoute d’abord une référence à l’objet COM au nom `com::ptr`de l’appelant, puis libère toutes les références appartenant à la .  L’appelant doit finalement libérer l’objet retourné pour le détruire.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé.  La `DetachDocument` fonction `Detach` membre appelle à renoncer à la propriété de l’objet COM et à retourner un pointeur à l’appelant.

```cpp
// comptr_detach.cpp
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

   // detach the COM object and return it
   // this releases the internal reference to the object
   IXMLDOMDocument* DetachDocument() {
      return m_ptrDoc.Detach();
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.DetachDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release document object as the ref class no longer owns it
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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>ptr::GetInterface

Retourne un pointeur sur l’objet COM possédé.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Valeur retournée

Un pointeur sur l’objet COM possédé.

### <a name="exceptions"></a>Exceptions

En `QueryInterface` interne, est appelé sur l’objet COM possédé et toute erreur `HRESULT` est convertie en une exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Notes

L’ajout `com::ptr` d’une référence à l’objet COM au nom de l’appelant et conserve également sa propre référence sur l’objet COM. L’appelant doit finalement publier la référence sur l’objet retourné ou il ne sera jamais détruit.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé. La `GetDocument` fonction `GetInterface` membre utilise pour retourner un pointeur à l’objet COM.

```cpp
// comptr_getinterface.cpp
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

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
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
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
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

```Output
<word>persnickety</word>
```

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>ptr::QueryInterface

Interroge l’objet COM possédé pour une interface `com::ptr`et attache le résultat à un autre .

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Le `com::ptr` qui obtiendra l’interface.

### <a name="exceptions"></a>Exceptions

En `QueryInterface` interne, est appelé sur l’objet COM possédé et toute erreur `HRESULT` est convertie en une exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour créer un emballage COM pour une interface différente de l’objet COM appartenant à l’emballage actuel. Cette méthode `QueryInterface` passe par l’objet COM possédé pour demander un pointeur à une interface spécifique `com::ptr`de l’objet COM et attache le pointeur d’interface retourné au passage.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé. La `WriteTopLevelNode` fonction `QueryInterface` membre utilise `com::ptr` pour `IXMLDOMNode` remplir un `com::ptr` local avec un, puis passe le (en suivant la référence) à une fonction membre privé qui écrit le nom du nœud et les propriétés de texte à la console.

```cpp
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

```Output
<#document>persnickety</#document>
```

## <a name="ptrrelease"></a><a name="release"></a>ptr::Libération

Communiqués toutes les références possédées sur l’objet COM.

```cpp
void Release();
```

### <a name="remarks"></a>Notes

L’appel de cette fonction libère toutes les références possédées `nullptr`sur l’objet COM et définit la poignée interne de l’objet COM à .  Si aucune autre référence sur l’objet COM n’existe, elle sera détruite.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé.  La `ReplaceDocument` fonction `Release` membre utilise pour libérer tout objet de document antérieur avant d’attacher le nouveau document.

```cpp
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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>ptr::opérateur-&gt;

Opérateur d’accès membre, utilisé pour appeler les méthodes sur l’objet COM appartenant.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Valeur retournée

A `smart_com_ptr` à l’objet COM.

### <a name="exceptions"></a>Exceptions

En `QueryInterface` interne, est appelé sur l’objet COM possédé et toute erreur `HRESULT` est convertie en une exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Notes

Cet opérateur vous permet d’appeler les méthodes de l’objet COM possédé. Il renvoie `smart_com_ptr` un temporaire qui `AddRef` `Release`gère automatiquement son propre et .

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé. La `WriteDocument` fonction `operator->` sert `get_firstChild` à appeler le membre de l’objet document.

```cpp
// comptr_op_member.cpp
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

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
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
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
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

```Output
<word>persnickety</word>
```

## <a name="ptroperator"></a><a name="operator-assign"></a>ptr::opérateur

Attache un objet COM `com::ptr`à un .

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Paramètres

*_right*<br/>
Le pointeur d’interface COM à attacher.

### <a name="return-value"></a>Valeur retournée

Une référence de `com::ptr`suivi sur le .

### <a name="exceptions"></a>Exceptions

Si `com::ptr` le possède déjà une référence `operator=` à <xref:System.InvalidOperationException>un objet COM, jette .

### <a name="remarks"></a>Notes

Attribuer un objet COM `com::ptr` à une référence de l’objet COM mais ne libère pas la référence de l’appelant.

Cet opérateur a le `Attach`même effet que .

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé.  La `ReplaceDocument` fonction membre `Release` fait d’abord appel `operator=` à tout objet précédemment possédé, puis utilise pour joindre un nouvel objet de document.

```cpp
// comptr_op_assign.cpp
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
      m_ptrDoc = pDoc;
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
      // store it in place of the one held by the ref class
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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>ptr::opérateur bool

Opérateur pour `com::ptr` l’utilisation dans une expression conditionnelle.

```cpp
operator bool();
```

### <a name="return-value"></a>Valeur retournée

`true`si l’objet COM possédé est valide; `false` autrement.

### <a name="remarks"></a>Notes

L’objet COM possédé est valide `nullptr`s’il ne l’est pas .

Cet opérateur se `_detail_class::_safe_bool` convertit `bool` à ce qui est plus sûr que parce qu’il ne peut pas être converti en un type intégral.

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé. La `CreateInstance` fonction `operator bool` membre utilise après la création du nouvel objet de document pour déterminer s’il est valide et écrit à la console si elle est.

```cpp
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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>ptr::opérateur!

opérateur pour déterminer si l’objet COM possédé est invalide.

```cpp
bool operator!();
```

### <a name="return-value"></a>Valeur retournée

`true`si l’objet COM possédé est invalide; `false` autrement.

### <a name="remarks"></a>Notes

L’objet COM possédé est valide `nullptr`s’il ne l’est pas .

### <a name="example"></a>Exemple

Cet exemple implémente une `com::ptr` classe CLR `IXMLDOMDocument` qui utilise un pour envelopper son objet membre privé.  La `CreateInstance` fonction `operator!` membre utilise pour déterminer si un objet document est déjà possédé, et ne crée une nouvelle instance que si l’objet est invalide.

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
