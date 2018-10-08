---
title: Attribut de programmation (FAQ) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a93dc67bd06f0dc88603643646fed3ad65052874
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790749"
---
# <a name="attribute-programming-faq"></a>Programmation par attributs (FAQ)

Cette rubrique répond les questions fréquemment posées suivantes :

- [Qu’est un HRESULT ?](#vcconattributeprogrammmingfaqanchor1)

- [Lorsque je dois spécifier le nom du paramètre pour un attribut ?](#vcconattributeprogrammmingfaqanchor2)

- [Puis-je utiliser des commentaires dans un bloc d’attributs ?](#vcconattributeprogrammmingfaqanchor3)

- [Comment les attributs interagissent-ils avec l’héritage ?](#vcconattributeprogrammmingfaqanchor4)

- [Comment puis-je utiliser les attributs dans un projet ATL sans attributs ?](#vcconattributeprogrammmingfaqanchor5)

- [Comment puis-je utiliser un fichier .idl dans un projet avec attributs ?](#vcconattributeprogrammmingfaqanchor6)

- [Puis-je modifier le code injecté par un attribut ?](#vcconattributeprogrammmingfaqanchor7)

- [Comment puis-je transférer déclarer une interface avec attributs ?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Puis-je utiliser des attributs sur une classe dérivée d’une classe qui utilise également des attributs ?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="vcconattributeprogrammmingfaqanchor1"></a> Qu’est un HRESULT ?

Un HRESULT est un type de données simple qui est souvent utilisé comme valeur de retour par des attributs et ATL en général. Le tableau suivant décrit les différentes valeurs. Plus de valeurs sont contenus dans le fichier d’en-tête winerror.h.

|Name|Description|Value|
|----------|-----------------|-----------|
|S_OK|Opération réussie|0x00000000|
|E_UNEXPECTED|Échec inattendu|0x8000ffff|
|E_NOTIMPL|Non implémenté|0 x 80004001|
|E_OUTOFMEMORY|Échec d’allocation de mémoire nécessaire|0x8007000E|
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valides|0 x 80070057|
|E_NOINTERFACE|Interface non pris en charge|0 x 80004002|
|E_POINTER|Pointeur non valide|0 x 80004003|
|E_HANDLE|Handle non valide|0x80070006|
|E_ABORT|Opération abandonnée|0 x 80004004|
|E_FAIL|Erreur non spécifiée|0 x 80004005|
|E_ACCESSDENIED|Accès général refusé|0 x 80070005|

##  <a name="vcconattributeprogrammmingfaqanchor2"></a> Lorsque je dois spécifier le nom du paramètre pour un attribut ?

Dans la plupart des cas, si l’attribut possède un seul paramètre, ce paramètre est nommé. Ce nom n’est pas obligatoire lors de l’insertion de l’attribut dans votre code. Par exemple, l’utilisation de la [agrégeable](aggregatable.md) attribut :

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

est exactement identique :

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Toutefois, les attributs suivants ont des paramètres uniques non nommés :

||||
|-|-|-|
|[call_as](call-as.md)|[case](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[entry](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[ID](id.md)|
|[iid_is](iid-is.md)|[import](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[source](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="vcconattributeprogrammmingfaqanchor3"></a> Puis-je utiliser des commentaires dans un bloc d’attributs ?

Vous pouvez utiliser des commentaires de ligne unique et plusieurs lignes dans un bloc d’attributs. Toutefois, vous ne pouvez pas utiliser un style de commentaire entre les parenthèses contenant les paramètres à un attribut.

Les éléments suivants sont autorisé :

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Ce qui suit n’est pas autorisé :

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)  
]
```

##  <a name="vcconattributeprogrammmingfaqanchor4"></a> Comment les attributs interagissent-ils avec l’héritage ?

Vous pouvez hériter de classes avec attributs et non attribuées à partir d’autres classes, qui peuvent eux-mêmes être attribués ou non. Le résultat de la dérivation à partir d’une classe avec attributs est identique à la dérivation à partir de cette classe une fois que le fournisseur d’attributs a transformé son code. Les attributs ne sont pas transmis aux classes dérivées par héritage de C++. Un fournisseur d’attributs transforme uniquement le code à proximité de ses attributs.

##  <a name="vcconattributeprogrammmingfaqanchor5"></a> Comment puis-je utiliser les attributs dans un projet ATL sans attributs ?

Avoir un projet ATL sans attributs, ce qui a un fichier .idl, et vous pouvez commencer à ajouter des objets avec attributs. Dans ce cas, utilisez le **Assistant Ajouter une classe** pour fournir le code.

##  <a name="vcconattributeprogrammmingfaqanchor6"></a> Comment puis-je utiliser un fichier .idl dans un projet avec attributs ?

Vous pouvez avoir un fichier .idl que vous souhaitez utiliser dans votre projet ATL avec attributs. Dans ce cas, vous utiliseriez le [importidl](importidl.md) , compilez le fichier .idl dans un fichier .h (consultez le [Pages de propriétés MIDL](../../ide/midl-property-pages.md) dans le projet **Pages de propriétés** boîte de dialogue), et puis inclure le fichier .h dans votre projet.

##  <a name="vcconattributeprogrammmingfaqanchor7"></a> Puis-je modifier le code injecté par un attribut ?

Certains attributs injectent du code dans votre projet. Vous pouvez voir le code injecté à l’aide de la [/Fx](../../build/reference/fx-merge-injected-code.md) option du compilateur. Il est également possible de copier le code à partir du fichier injecté et collez-le dans votre code source. Cela vous permet de modifier le comportement de l’attribut. Toutefois, vous devrez peut-être modifier d’autres parties de votre code ainsi.

L’exemple suivant est le résultat de la copie du code injecté dans un fichier de code source :

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)  
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")  
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")  
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()  
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))  
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)  
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))  
END_CONNECTION_POINT_MAP()  
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> Comment puis-je transférer déclarer une interface avec attributs ?

Si vous vous apprêtez à effectuer une déclaration anticipée d’une interface avec attributs, vous devez appliquer les mêmes attributs à la déclaration anticipée que vous appliquez à la déclaration d’interface réelle. Vous devez également appliquer le [exporter](export.md) attribut votre déclaration anticipée.

##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> Puis-je utiliser des attributs sur une classe dérivée d’une classe qui utilise également des attributs ?

Non, à l’aide des attributs sur une classe dérivée d’une classe qui utilise également des attributs n’est pas pris en charge.

## <a name="see-also"></a>Voir aussi

[Attributs de C++ pour COM et .NET](cpp-attributes-com-net.md)