---
title: Erreur du compilateur C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: 4a1d46f3b000b5054564b05ca2c3c94a9e7b6398
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479283"
---
# <a name="compiler-error-c2666"></a>Erreur du compilateur C2666

'identificateur' : nombre surcharges ont des conversions similaires

Une fonction surchargée ou un opérateur est ambigu.   Listes de paramètres formels peuvent être trop similaires pour le compilateur résoudre l’ambiguïté.  Pour résoudre cette erreur, caster explicitement un ou plusieurs des paramètres réels.

L’exemple suivant génère l’erreur C2666 :

```
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

Cette erreur peut également être due à la mise en conformité du compilateur pour Visual Studio .NET 2003 :

- opérateurs binaires et conversions définies par l’utilisateur en types pointeur

- conversion de qualification n’est pas identique à la conversion d’identité

Pour les opérateurs binaires \<, >, \<=, et > =, un passé paramètre est maintenant implicitement converti vers le type de l’opérande si le type du paramètre définit un opérateur de conversion définie par l’utilisateur pour convertir le type de l’opérande. Il existe désormais risque d’ambiguïté.

Pour le code qui est valide dans les versions de Visual Studio .NET de Visual C++ et de Visual Studio .NET 2003, appelez l’opérateur de classe explicitement à l’aide de la syntaxe de la fonction.

## <a name="example"></a>Exemple

```
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

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2666

```
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