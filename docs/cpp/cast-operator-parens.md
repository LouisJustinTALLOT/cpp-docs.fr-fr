---
title: 'Opérateur de cast : ()'
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators [C++]
- () cast operator
ms.assetid: 4c99eb92-1b19-4a5d-9840-5d8c29b8453e
ms.openlocfilehash: 491e8ea3bc3ff81e88825700de6a549324a0d5af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190155"
---
# <a name="cast-operator-"></a>Opérateur de cast : ()

Un cast de type fournit une méthode pour la conversion explicite du type d'un objet dans une situation spécifique.

## <a name="syntax"></a>Syntaxe

```
unary-expression ( type-name ) cast-expression
```

## <a name="remarks"></a>Notes

Toute expression unaire est considérée comme une expression de cast.

Le compilateur traite *cast-expression* comme le type *type-name* après la réalisation d'un cast de type. Les casts peuvent être utilisés pour convertir des objets de tout type scalaire vers ou depuis tout autre type scalaire. Les casts de types explicites sont contraints par les mêmes règles qui déterminent les effets des conversions implicites. Les restrictions supplémentaires sur les casts peuvent résulter des tailles réelles ou de la représentation des types spécifiques.

## <a name="example"></a>Exemple

```cpp
// expre_CastOperator.cpp
// compile with: /EHsc
// Demonstrate cast operator
#include <iostream>

using namespace std;

int main()
{
    double x = 3.1;
    int i;
    cout << "x = " << x << endl;
    i = (int)x;   // assign i the integer part of x
    cout << "i = " << i << endl;
}
```

## <a name="example"></a>Exemple

```cpp
// expre_CastOperator2.cpp
// The following sample shows how to define and use a cast operator.
#include <string.h>
#include <stdio.h>

class CountedAnsiString
{
public:
    // Assume source is not null terminated
    CountedAnsiString(const char *pStr, size_t nSize) :
                      m_nSize(nSize)
    {
        m_pStr = new char[sizeOfBuffer];

        strncpy_s(m_pStr, sizeOfBuffer, pStr, m_nSize);
        memset(&m_pStr[m_nSize], '!', 9); // for demonstration purposes.
    }

    // Various string-like methods...

    const char *GetRawBytes() const
    {
        return(m_pStr);
    }

    //
    // operator to cast to a const char *
    //
    operator const char *()
    {
        m_pStr[m_nSize] = '\0';
        return(m_pStr);
    }

    enum
    {
        sizeOfBuffer = 20
    } size;

private:
    char *m_pStr;
    const size_t m_nSize;
};

int main()
{
    const char *kStr = "Excitinggg";
    CountedAnsiString myStr(kStr, 8);

    const char *pRaw = myStr.GetRawBytes();
    printf_s("RawBytes truncated to 10 chars:   %.10s\n", pRaw);

    const char *pCast = myStr; // or (const char *)myStr;
    printf_s("Casted Bytes:   %s\n", pCast);

    puts("Note that the cast changed the raw internal string");
    printf_s("Raw Bytes after cast:   %s\n", pRaw);
}
```

```Output
RawBytes truncated to 10 chars:   Exciting!!
Casted Bytes:   Exciting
Note that the cast changed the raw internal string
Raw Bytes after cast:   Exciting
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateur de conversion de type explicite](../cpp/explicit-type-conversion-operator-parens.md)<br/>
[Opérateurs de casting](../cpp/casting-operators.md)<br/>
[Opérateurs de cast](../c-language/cast-operators.md)
