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
ms.openlocfilehash: 9cb0ad23450d06bb314b0e2d6fa1d01784d633e2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214904"
---
# <a name="comptr-class"></a>com::ptr, classe

Wrapper pour un objet COM qui peut être utilisé en tant que membre d’une classe CLR.  Le wrapper automatise également la gestion de la durée de vie de l’objet COM, en libérant toutes les références appartenant à l’objet lorsque son destructeur est appelé. Analogue à la [classe CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntaxe

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Paramètres

*_interface_type*<br/>
Interface COM.

## <a name="remarks"></a>Notes

Un `com::ptr` peut également être utilisé comme variable de fonction locale pour simplifier diverses tâches com et automatiser la gestion de la durée de vie.

Un `com::ptr` ne peut pas être utilisé directement comme paramètre de fonction ; utilisez à la place un [opérateur de référence de suivi](../extensions/tracking-reference-operator-cpp-component-extensions.md) ou un [handle vers l’opérateur d’objet (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) .

Un `com::ptr` ne peut pas être retourné directement à partir d’une fonction ; utilisez un handle à la place.

## <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé.  L’appel des méthodes publiques de la classe entraîne des appels à l' `IXMLDOMDocument` objet contenu.  L’exemple crée une instance d’un document XML, le remplit avec un code XML simple et effectue une procédure simplifiée des nœuds dans l’arborescence de documents analysés pour imprimer le XML sur la console.

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
|[ptr ::p tr](#ptr)|Construit un `com::ptr` pour encapsuler un objet com.|
|[ptr::~ptr](#tilde-ptr)|Détruit un `com::ptr` .|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|---------|-----------|
|[ptr::Attach](#attach)|Joint un objet COM à un `com::ptr` .|
|[ptr::CreateInstance](#createInstance)|Crée une instance d’un objet COM dans un `com::ptr` .|
|[ptr::Detach](#detach)|Donne la propriété de l’objet COM, en retournant un pointeur vers l’objet.|
|[ptr::GetInterface](#getInterface)|Crée une instance d’un objet COM dans un `com::ptr` .|
|[ptr::QueryInterface](#queryInterface)|Interroge l’objet COM détenu pour une interface et joint le résultat à un autre objet `com::ptr` .|
|[ptr::Release](#release)|Libère toutes les références appartenant à l’objet COM.|

### <a name="public-operators"></a>Opérateurs publics

|Nom|Description|
|---------|-----------|
|[ptr :: Operator-&gt;](#operator-arrow)|Opérateur d’accès aux membres, utilisé pour appeler des méthodes sur l’objet COM détenu.|
|[ptr :: Operator =](#operator-assign)|Joint un objet COM à un `com::ptr` .|
|[ptr :: Operator &nbsp; bool](#operator-bool)|Opérateur à utiliser `com::ptr` dans une expression conditionnelle.|
|[ptr::operator!](#operator-logical-not)|Pour déterminer si l’objet COM détenu n’est pas valide.|

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<msclr\com\ptr.h>

**Espace de noms** msclr, :: com

## <a name="ptrptr"></a><a name="ptr"></a>ptr ::p tr

Retourne un pointeur vers l’objet COM détenu.

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

Le constructeur sans argument affecte **`nullptr`** au handle d’objet sous-jacent. Les appels futurs à l' `com::ptr` valideront l’objet interne et échoueront silencieusement jusqu’à ce qu’un objet soit créé ou attaché.

Le constructeur à un argument ajoute une référence à l’objet COM, mais ne libère pas la référence de l’appelant. par conséquent, l’appelant doit appeler `Release` sur l’objet com pour abandonner véritablement le contrôle. Lorsque le `com::ptr` destructeur de est appelé, il libère automatiquement ses références sur l’objet com.

`NULL`Le passage à ce constructeur revient à appeler la version sans argument.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé. Il illustre l’utilisation des deux versions du constructeur.

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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>ptr :: ~ PTR

Détruit un `com::ptr` .

```cpp
~ptr();
```

### <a name="remarks"></a>Notes

En cas de destruction, `com::ptr` libère toutes les références qu’il possède à son objet com. En supposant qu’il n’existe aucune autre référence dans l’objet COM, l’objet COM sera supprimé et sa mémoire libérée.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé.  Dans la `main` fonction, les deux `XmlDocument` destructeurs d’objets sont appelés lorsqu’ils sortent de la portée du **`try`** bloc, ce qui entraîne l’appel du destructeur sous-jacent `com::ptr` , en libérant toutes les références appartenant à l’objet com.

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

## <a name="ptrattach"></a><a name="attach"></a>ptr :: Attach

Joint un objet COM à un `com::ptr` .

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Paramètres

*_right*<br/>
Pointeur d’interface COM à attacher.

### <a name="exceptions"></a>Exceptions

Si le `com::ptr` possède déjà une référence à un objet com, `Attach` lève une exception <xref:System.InvalidOperationException> .

### <a name="remarks"></a>Notes

Un appel à `Attach` fait référence à l’objet com, mais ne libère pas la référence de l’appelant.

Le passage `NULL` à `Attach` n’entraîne aucune action en cours.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé. La `ReplaceDocument` fonction membre appelle d’abord `Release` sur tout objet détenu précédemment, puis appelle `Attach` pour joindre un nouvel objet document.

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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>ptr :: CreateInstance

Crée une instance d’un objet COM dans un `com::ptr` .

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

*ProgID*<br/>
Chaîne `ProgID`.

*pouter*<br/>
Pointeur vers l’interface IUnknown de l’objet d’agrégation (contrôle IUnknown). Si `pouter` n’est pas spécifié, `NULL` est utilisé.

*cls_context*<br/>
Contexte dans lequel le code qui gère l’objet nouvellement créé s’exécutera. Les valeurs sont extraites de l' `CLSCTX` énumération. Si `cls_context` n’est pas spécifié, la valeur CLSCTX_ALL est utilisée.

*rclsid*<br/>
`CLSID`associé aux données et au code qui seront utilisés pour créer l’objet.

### <a name="exceptions"></a>Exceptions

Si le `com::ptr` possède déjà une référence à un objet com, `CreateInstance` lève une exception <xref:System.InvalidOperationException> .

Cette fonction appelle `CoCreateInstance` et utilise <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pour convertir une erreur `HRESULT` en une exception appropriée.

### <a name="remarks"></a>Notes

`CreateInstance`utilise `CoCreateInstance` pour créer une nouvelle instance de l’objet spécifié, identifiée à partir d’un ProgID ou d’un CLSID. Le `com::ptr` référence l’objet nouvellement créé et libère automatiquement toutes les références détenues lors de la destruction.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé. Les constructeurs de classe utilisent deux formes différentes de `CreateInstance` pour créer l’objet de document à partir d’un ProgID ou d’un CLSID, ainsi que d’un CLSCTX.

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

## <a name="ptrdetach"></a><a name="detach"></a>ptr ::D Etach

Donne la propriété de l’objet COM, en retournant un pointeur vers l’objet.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Valeur retournée

Pointeur vers l’objet COM.

Si aucun objet n’est détenu, la valeur NULL est retournée.

### <a name="exceptions"></a>Exceptions

En interne, `QueryInterface` est appelé sur l’objet com détenu et toute erreur `HRESULT` est convertie en exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>Notes

`Detach`Ajoute d’abord une référence à l’objet COM pour le compte de l’appelant, puis libère toutes les références détenues par le `com::ptr` .  L’appelant doit finalement libérer l’objet retourné pour le détruire.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé.  La `DetachDocument` fonction membre appelle `Detach` pour abandonner la propriété de l’objet com et retourner un pointeur vers l’appelant.

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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>ptr :: GetInterface

Retourne un pointeur vers l’objet COM détenu.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Valeur retournée

Pointeur vers l’objet COM détenu.

### <a name="exceptions"></a>Exceptions

En interne, `QueryInterface` est appelé sur l’objet com détenu et toute erreur `HRESULT` est convertie en exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>Notes

`com::ptr`Ajoute une référence à l’objet com au nom de l’appelant et conserve également sa propre référence sur l’objet com. L’appelant doit finalement libérer la référence sur l’objet retourné ou il ne sera jamais détruit.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé. La `GetDocument` fonction membre utilise `GetInterface` pour retourner un pointeur vers l’objet com.

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

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>ptr :: QueryInterface

Interroge l’objet COM détenu pour une interface et joint le résultat à un autre objet `com::ptr` .

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
`com::ptr`Qui obtiendra l’interface.

### <a name="exceptions"></a>Exceptions

En interne, `QueryInterface` est appelé sur l’objet com détenu et toute erreur `HRESULT` est convertie en exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>Notes

Utilisez cette méthode pour créer un wrapper COM pour une interface différente de l’objet COM possédé par le wrapper actuel. Cette méthode appelle `QueryInterface` via l’objet com détenu pour demander un pointeur vers une interface spécifique de l’objet com et attache le pointeur d’interface retourné au passé `com::ptr` .

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé. La `WriteTopLevelNode` fonction membre utilise `QueryInterface` pour remplir un local `com::ptr` avec un `IXMLDOMNode` , puis passe `com::ptr` (par référence de suivi) à une fonction membre privée qui écrit les propriétés Name et Text du nœud dans la console.

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

## <a name="ptrrelease"></a><a name="release"></a>ptr :: Release

Libère toutes les références appartenant à l’objet COM.

```cpp
void Release();
```

### <a name="remarks"></a>Notes

L’appel de cette fonction libère toutes les références appartenant à l’objet COM et définit le handle interne de l’objet COM sur **`nullptr`** .  S’il n’existe aucune autre référence sur l’objet COM, il sera détruit.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé.  La `ReplaceDocument` fonction membre utilise `Release` pour libérer tout objet document précédent avant d’attacher le nouveau document.

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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>ptr :: Operator-&gt;

Opérateur d’accès aux membres, utilisé pour appeler des méthodes sur l’objet COM détenu.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Valeur retournée

`smart_com_ptr`À l’objet com.

### <a name="exceptions"></a>Exceptions

En interne, `QueryInterface` est appelé sur l’objet com détenu et toute erreur `HRESULT` est convertie en exception par <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>Notes

Cet opérateur vous permet d’appeler des méthodes de l’objet COM détenu. Elle retourne un temporaire `smart_com_ptr` qui gère automatiquement ses propres `AddRef` et `Release` .

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé. La `WriteDocument` fonction utilise `operator->` pour appeler le `get_firstChild` membre de l’objet document.

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

## <a name="ptroperator"></a><a name="operator-assign"></a>ptr :: Operator =

Joint un objet COM à un `com::ptr` .

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Paramètres

*_right*<br/>
Pointeur d’interface COM à attacher.

### <a name="return-value"></a>Valeur retournée

Référence de suivi sur le `com::ptr` .

### <a name="exceptions"></a>Exceptions

Si le `com::ptr` possède déjà une référence à un objet com, `operator=` lève une exception <xref:System.InvalidOperationException> .

### <a name="remarks"></a>Notes

L’assignation d’un objet COM à un `com::ptr` référence l’objet com, mais ne libère pas la référence de l’appelant.

Cet opérateur a le même effet que `Attach` .

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé.  La `ReplaceDocument` fonction membre appelle d’abord `Release` sur tout objet détenu précédemment, puis utilise `operator=` pour attacher un nouvel objet document.

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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>ptr :: operator bool

Opérateur à utiliser `com::ptr` dans une expression conditionnelle.

```cpp
operator bool();
```

### <a name="return-value"></a>Valeur retournée

**`true`** Si l’objet COM détenu est valide ; **`false`** sinon,.

### <a name="remarks"></a>Notes

L’objet COM détenu est valide si ce n’est pas le cas **`nullptr`** .

Cet opérateur convertit vers `_detail_class::_safe_bool` qui est plus sûr que **`bool`** parce qu’il ne peut pas être converti en un type intégral.

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé. La `CreateInstance` fonction membre utilise `operator bool` après avoir créé le nouvel objet document pour déterminer si elle est valide et écrit dans la console si elle est.

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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>ptr :: Operator !

Pour déterminer si l’objet COM détenu n’est pas valide.

```cpp
bool operator!();
```

### <a name="return-value"></a>Valeur retournée

**`true`** Si l’objet COM détenu n’est pas valide ; **`false`** sinon,.

### <a name="remarks"></a>Notes

L’objet COM détenu est valide si ce n’est pas le cas **`nullptr`** .

### <a name="example"></a>Exemple

Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son `IXMLDOMDocument` objet membre privé.  La `CreateInstance` fonction membre utilise `operator!` pour déterminer si un objet document est déjà détenu et crée uniquement une nouvelle instance si l’objet n’est pas valide.

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
