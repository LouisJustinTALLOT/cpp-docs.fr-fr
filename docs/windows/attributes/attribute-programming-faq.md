---
title: Programmation par attributs (FAQ)
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 6c1762994d2cb109e86397bb0a5db1258cf33be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376064"
---
# <a name="attribute-programming-faq"></a>Programmation par attributs (FAQ)

Ce sujet répond aux questions suivantes fréquemment posées :

- [Qu’est-ce qu’un HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Quand dois-je spécifier le nom du paramètre pour un attribut ?](#vcconattributeprogrammmingfaqanchor2)

- [Puis-je utiliser des commentaires dans un bloc d’attributs ?](#vcconattributeprogrammmingfaqanchor3)

- [Comment les attributs interagissent-ils avec l’héritage ?](#vcconattributeprogrammmingfaqanchor4)

- [Comment puis-je utiliser des attributs dans un projet ATL non attribué ?](#vcconattributeprogrammmingfaqanchor5)

- [Comment puis-je utiliser un fichier .idl dans un projet attribué?](#vcconattributeprogrammmingfaqanchor6)

- [Puis-je modifier le code injecté par un attribut ?](#vcconattributeprogrammmingfaqanchor7)

- [Comment puis-je déclarer en avant une interface attribuée ?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Puis-je utiliser des attributs sur une classe dérivée d’une classe qui utilise également des attributs ?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>Qu’est-ce qu’un HRESULT?

Un HRESULT est un type de données simple qui est souvent utilisé comme valeur de retour par attributs et ATL en général. Le tableau suivant décrit les différentes valeurs. Plus de valeurs sont contenues dans le fichier d’en-tête winerror.h.

|Nom|Description|Valeur|
|----------|-----------------|-----------|
|S_OK|L’opération a réussi|0x00000000|
|E_UNEXPECTED|Échec inattendu|0x8000FFFF|
|E_NOTIMPL|Non implémenté|0x80004001|
|E_OUTOFMEMORY|Échec de l’attribution de la mémoire nécessaire|0x8007000E|
|E_INVALIDARG|Un ou plusieurs arguments sont invalides|0x80070057|
|E_NOINTERFACE|Interface non prise en charge|0x80004002|
|E_POINTER|Pointeur invalide|0x80004003|
|E_HANDLE|Poignée invalide|0x80070006|
|E_ABORT|Opération avortée|0x80004004|
|E_FAIL|Échec non spécifié|0x80004005|
|E_ACCESSDENIED|Accès général refusé par erreur|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>Quand dois-je spécifier le nom du paramètre pour un attribut ?

Dans la plupart des cas, si l’attribut a un seul paramètre, ce paramètre est nommé. Ce nom n’est pas nécessaire lors de l’insertion de l’attribut dans votre code. Par exemple, l’utilisation suivante de [l’attribut aggregatable](aggregatable.md) :

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

est exactement le même que:

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Cependant, les attributs suivants ont des paramètres uniques et anonymes :

||||
|-|-|-|
|[call_as](call-as.md)|[Cas](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[Par défaut](default-cpp.md)|[Defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[Entrée](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[Importation](import.md)|[importlib](importlib.md)|
|[Inclure](include-cpp.md)|[inclurelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[Restreint](restricted.md)|
|[size_is](size-is.md)|[Source](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>Puis-je utiliser des commentaires dans un bloc d’attributs ?

Vous pouvez utiliser des commentaires à ligne unique et à plusieurs lignes dans un bloc d’attributs. Cependant, vous ne pouvez pas utiliser l’un ou l’autre style de commentaire dans les parenthèses tenant les paramètres à un attribut.

Ce qui suit est autorisé :

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Ce qui suit est refusé :

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>Comment les attributs interagissent-ils avec l’héritage ?

Vous pouvez hériter à la fois des classes attribuées et non attribuées d’autres classes, qui peuvent elles-mêmes être attribuées ou non. Le résultat de la dérivant d’une classe attribuée est le même que de dérivé de cette classe après que le fournisseur d’attributs a transformé son code. Les attributs ne sont pas transmis aux classes dérivées par l’héritage de C. Un fournisseur d’attributs ne transforme le code qu’à proximité de ses attributs.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>Comment puis-je utiliser des attributs dans un projet ATL non attribué ?

Vous pouvez avoir un projet ATL non attribué, qui a un fichier .idl, et vous pouvez commencer à ajouter des objets attribués. Dans ce cas, utilisez le **Assistant de classe Add** pour fournir le code.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>Comment puis-je utiliser un fichier .idl dans un projet attribué?

Vous pouvez avoir un fichier .idl que vous souhaitez utiliser dans votre projet ATL attribué. Dans ce cas, vous utiliseriez l’attribut [importidl,](importidl.md) compilez le fichier .idl à un fichier .h (voir les [pages de propriété MIDL](../../build/reference/midl-property-pages.md) dans la boîte de dialogue **des pages de propriété** du projet), puis incluriez le fichier .h dans votre projet.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>Puis-je modifier le code injecté par un attribut ?

Certains attributs injectent du code dans votre projet. Vous pouvez voir le code injecté en utilisant l’option [compilateur /Fx.](../../build/reference/fx-merge-injected-code.md) Il est également possible de copier le code à partir du fichier injecté et de le coller dans votre code source. Cela vous permet de modifier le comportement de l’attribut. Cependant, vous devrez peut-être modifier d’autres parties de votre code ainsi.

L’échantillon suivant est le résultat de la copie du code injecté dans un fichier de code source :

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>Comment puis-je déclarer en avant une interface attribuée ?

Si vous devez faire une déclaration à terme d’une interface attribuée, vous devez appliquer les mêmes attributs à la déclaration prospective que vous appliquez à la déclaration d’interface réelle. Vous devez également appliquer l’attribut [d’exportation](export.md) à votre déclaration à terme.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>Puis-je utiliser des attributs sur une classe dérivée d’une classe qui utilise également des attributs ?

Non, l’utilisation d’attributs sur une classe dérivée d’une classe qui utilise également des attributs n’est pas prise en charge.

## <a name="see-also"></a>Voir aussi

[Attributs C++ pour COM et .NET](cpp-attributes-com-net.md)
