---
description: 'En savoir plus sur : FAQ sur la programmation des attributs'
title: Programmation par attributs (FAQ)
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 7a3bdfc8749297d11c5bc33b706265a1f5913a69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240427"
---
# <a name="attribute-programming-faq"></a>Programmation par attributs (FAQ)

Cette rubrique répond aux questions fréquemment posées suivantes :

- [Qu’est-ce qu’un HRESULT ?](#vcconattributeprogrammmingfaqanchor1)

- [Quand dois-je spécifier le nom de paramètre d’un attribut ?](#vcconattributeprogrammmingfaqanchor2)

- [Puis-je utiliser des commentaires dans un bloc d’attributs ?](#vcconattributeprogrammmingfaqanchor3)

- [Comment les attributs interagissent-ils avec l’héritage ?](#vcconattributeprogrammmingfaqanchor4)

- [Comment puis-je utiliser des attributs dans un projet ATL sans attribut ?](#vcconattributeprogrammmingfaqanchor5)

- [Comment puis-je utiliser un fichier. idl dans un projet avec attributs ?](#vcconattributeprogrammmingfaqanchor6)

- [Puis-je modifier le code injecté par un attribut ?](#vcconattributeprogrammmingfaqanchor7)

- [Comment puis-je déclarer une interface avec attributs ?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Puis-je utiliser des attributs sur une classe dérivée d’une classe qui utilise également des attributs ?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a> Qu’est-ce qu’un HRESULT ?

Un HRESULT est un type de données simple qui est souvent utilisé comme valeur de retour par les attributs et les ATL en général. Le tableau suivant décrit les différentes valeurs. D’autres valeurs sont contenues dans le fichier d’en-tête winerror. h.

|Nom|Description|Valeur|
|----------|-----------------|-----------|
|S_OK|L’opération a réussi|0x00000000|
|E_UNEXPECTED|Défaillance inattendue|0x8000FFFF|
|E_NOTIMPL|Non implémenté|0x80004001|
|E_OUTOFMEMORY|Échec de l’allocation de mémoire nécessaire|0x8007000E|
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valides|0x80070057|
|E_NOINTERFACE|Interface non prise en charge|0x80004002|
|E_POINTER|Pointeur non valide|0x80004003|
|E_HANDLE|Handle non valide|0x80070006|
|E_ABORT|Opération abandonnée|0x80004004|
|E_FAIL|Échec non spécifié|0x80004005|
|E_ACCESSDENIED|Erreur d’accès général refusé|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a> Quand dois-je spécifier le nom de paramètre d’un attribut ?

Dans la plupart des cas, si l’attribut a un seul paramètre, ce paramètre est nommé. Ce nom n’est pas requis lors de l’insertion de l’attribut dans votre code. Par exemple, l’utilisation suivante de l’attribut [agrégeables](aggregatable.md) :

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

est exactement le même que :

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Toutefois, les attributs suivants ont des paramètres sans nom uniques :

:::row:::
   :::column span="":::
      [`call_as`](call-as.md)\
      [`case`](case-cpp.md)\
      [`cpp_quote`](cpp-quote.md)\
      [`default`](default-cpp.md)\
      [`defaultvalue`](defaultvalue.md)\
      [`defaultvtable`](defaultvtable.md)\
      [`emitidl`](emitidl.md)\
      [`entry`](entry.md)\
      [`first_is`](first-is.md)
   :::column-end:::
   :::column span="":::
      [`helpcontext`](helpcontext.md)\
      [`helpfile`](helpfile.md)\
      [`helpstring`](helpstring.md)\
      [`helpstringcontext`](helpstringcontext.md)\
      [`helpstringdll`](helpstringdll.md)\
      [`id`](id.md)\
      [`iid_is`](iid-is.md)\
      [`import`](import.md)
   :::column-end:::
   :::column span="":::
      [`importlib`](importlib.md)\
      [`include`](include-cpp.md)\
      [`includelib`](includelib-cpp.md)\
      [`last_is`](last-is.md)\
      [`length_is`](length-is.md)\
      [`max_is`](max-is.md)\
      [`no_injected_text`](no-injected-text.md)\
      [`pointer_default`](pointer-default.md)
   :::column-end:::
   :::column span="":::
      [`pragma`](pragma.md)\
      [`restricted`](restricted.md)\
      [`size_is`](size-is.md)\
      [`source`](source-cpp.md)\
      [`switch_is`](switch-is.md)\
      [`switch_type`](switch-type.md)\
      [`transmit_as`](transmit-as.md)\
      [`wire_marshal`](wire-marshal.md)
   :::column-end:::
:::row-end:::

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a> Puis-je utiliser des commentaires dans un bloc d’attributs ?

Vous pouvez utiliser des commentaires sur une seule ligne et sur plusieurs lignes dans un bloc d’attributs. Toutefois, vous ne pouvez pas utiliser l’un ou l’autre style de commentaire entre parenthèses contenant les paramètres d’un attribut.

Les éléments suivants sont autorisés :

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Les éléments suivants ne sont pas autorisés :

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a> Comment les attributs interagissent-ils avec l’héritage ?

Vous pouvez hériter des classes avec ou sans attributs d’autres classes, qui peuvent elles-mêmes être attribuées ou non. Le résultat de la dérivation à partir d’une classe avec attributs est identique à la dérivation de cette classe après que le fournisseur d’attributs a transformé son code. Les attributs ne sont pas transmis aux classes dérivées par le biais de l’héritage C++. Un fournisseur d’attributs transforme uniquement le code à proximité de ses attributs.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a> Comment puis-je utiliser des attributs dans un projet ATL sans attribut ?

Vous pouvez avoir un projet ATL sans attribut, qui contient un fichier. idl, et vous pouvez commencer à ajouter des objets avec attributs. Dans ce cas, utilisez l' **Assistant Ajout** d’une classe pour fournir le code.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a> Comment puis-je utiliser un fichier. idl dans un projet avec attributs ?

Vous avez peut-être un fichier. idl que vous souhaitez utiliser dans votre projet avec attributs ATL. Dans ce cas, vous utilisez l’attribut [importidl](importidl.md) , compilez le fichier. idl dans un fichier. h (consultez les [pages de propriétés MIDL](../../build/reference/midl-property-pages.md) dans la boîte de dialogue **pages de propriétés** du projet), puis incluez le fichier. h dans votre projet.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a> Puis-je modifier le code injecté par un attribut ?

Certains attributs injectent du code dans votre projet. Vous pouvez voir le code injecté en utilisant l’option de compilateur [/FX](../../build/reference/fx-merge-injected-code.md) . Il est également possible de copier du code à partir du fichier injecté et de le coller dans votre code source. Cela vous permet de modifier le comportement de l’attribut. Toutefois, vous devrez peut-être modifier également d’autres parties de votre code.

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> Comment puis-je déclarer une interface avec attributs ?

Si vous envisagez de créer une déclaration anticipée d’une interface avec attributs, vous devez appliquer les mêmes attributs à la déclaration anticipée que vous appliquez à la déclaration d’interface réelle. Vous devez également appliquer l’attribut [Export](export.md) à votre déclaration anticipée.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> Puis-je utiliser des attributs sur une classe dérivée d’une classe qui utilise également des attributs ?

Non, l’utilisation d’attributs sur une classe dérivée d’une classe qui utilise également des attributs n’est pas prise en charge.

## <a name="see-also"></a>Voir aussi

[Attributs C++ pour COM et .NET](cpp-attributes-com-net.md)
