---
description: 'En savoir plus sur : erreur du compilateur C2666'
title: Erreur du compilateur C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: bfee8a2cb62f351d7d09faa499f1a936d14ea813
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210814"
---
# <a name="compiler-error-c2666"></a>Erreur du compilateur C2666

'identificateur' : les surcharges numériques ont des conversions similaires

Une fonction ou un opérateur surchargé est ambigu.   Les listes de paramètres formels peuvent être trop similaires pour que le compilateur puisse résoudre l’ambiguïté.  Pour résoudre cette erreur, effectuez un cast explicite d’un ou plusieurs des paramètres réels.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2666 :

```cpp
// C2666.cpp
struct complex {
   complex(double);
};

void h(int,complex);
void h(double, double);

int main() {
   h(3,4);   // C2666
}
```

Cette erreur peut également être générée en raison du travail de conformité du compilateur pour Visual Studio .NET 2003 :

- opérateurs binaires et conversions définies par l’utilisateur en types pointeur

- la conversion de qualification n’est pas la même que la conversion d’identité

Pour les opérateurs binaires \<, > , \<=, and > =, un paramètre passé est désormais implicitement converti en type de l’opérande si le type du paramètre définit un opérateur de conversion défini par l’utilisateur à convertir en type de l’opérande. Il existe désormais un potentiel d’ambiguïté.

Pour obtenir un code valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, appelez l’opérateur de classe explicitement à l’aide de la syntaxe de fonction.

```cpp
// C2666b.cpp
#include <string.h>
#include <stdio.h>

struct T
{
    T( const T& copy )
    {
        m_str = copy.m_str;
    }

    T( const char* str )
    {
        int iSize = (strlen( str )+ 1);
        m_str = new char[ iSize ];
        if (m_str)
            strcpy_s( m_str, iSize, str );
    }

    bool operator<( const T& RHS )
    {
        return m_str < RHS.m_str;
    }

    operator char*() const
    {
        return m_str;
    }

    char* m_str;
};

int main()
{
    T str1( "ABCD" );
    const char* str2 = "DEFG";

    // Error - Ambiguous call to operator<()
    // Trying to convert str1 to char* and then call
    // operator<( const char*, const char* )?
    //  OR
    // trying to convert str2 to T and then call
    // T::operator<( const T& )?

    if( str1 < str2 )   // C2666

    if ( str1.operator < ( str2 ) )   // Treat str2 as type T
        printf_s("str1.operator < ( str2 )\n");

    if ( str1.operator char*() < str2 )   // Treat str1 as type char*
        printf_s("str1.operator char*() < str2\n");
}
```

L’exemple suivant génère l’C2666

```cpp
// C2666c.cpp
// compile with: /c

enum E
{
    E_A,   E_B
};

class A
{
    int h(const E e) const {return 0; }
    int h(const int i) { return 1; }
    // Uncomment the following line to resolve.
    // int h(const E e) { return 0; }

    void Test()
    {
        h(E_A);   // C2666
        h((const int) E_A);
        h((int) E_A);
    }
};
```
