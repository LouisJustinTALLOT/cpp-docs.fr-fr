---
title: __interface
ms.date: 11/04/2016
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 1ec3a1d2cddbf8dbbb248a7366d5d56dd95ad074
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768313"
---
# <a name="interface"></a>__interface

**Section spécifique à Microsoft**

Une interface Visual C++ peut être définie comme suit :

- Peut hériter de zéro ou plusieurs interfaces de base.

- Ne peut pas hériter d'une classe de base.

- Ne peut contenir que des méthodes publiques, virtuelles pures.

- Ne peut pas contenir de constructeurs, de destructeurs ou d'opérateurs.

- Ne peut pas contenir de méthodes statiques.

- Ne peut pas contenir de données membres ; les propriétés sont autorisées.

## <a name="syntax"></a>Syntaxe

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Notes

Un C++ [classe](../cpp/class-cpp.md) ou [struct](../cpp/struct-cpp.md) pourrait être implémenté avec ces règles, mais **__interface** les applique.

Par exemple, voici un exemple de définition d'interface :

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Pour plus d’informations sur les interfaces managées, consultez [classe d’interface](../extensions/interface-class-cpp-component-extensions.md).

Notez que vous n'êtes pas obligé d'indiquer explicitement que `CommitX` et `get_X` sont des fonctions virtuelles pures. Une déclaration équivalente pour la première fonction se présenterait comme suit :

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface** implique la [novtable](../cpp/novtable.md) **__declspec** modificateur.

## <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser les propriétés déclarées dans une interface.

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Attributs d’interface](../windows/attributes/interface-attributes.md)