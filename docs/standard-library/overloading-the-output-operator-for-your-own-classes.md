---
title: Surcharge de l’opérateur &lt;&lt; pour vos propres classes
ms.date: 11/04/2016
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
ms.openlocfilehash: 290491f7afb22873d60abb6662b470d8e7abefc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370682"
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Surcharge de l’opérateur &lt;&lt; pour vos propres classes

Les flux de sortie utilisent l’opérateur d’insertion (`<<`) pour les types standard. Vous pouvez aussi surcharger l’opérateur `<<` pour vos propres classes.

## <a name="example"></a>Exemple

L’exemple de fonction `write` a montré l’utilisation d’une structure `Date`. Les dates sont une parfaite illustration de classe C++ dans laquelle les membres de données (mois, jour et année) sont masqués. Un flux de sortie est la destination logique pour l’affichage d’une structure de ce type. Ce code affiche une date à l’aide de l’objet `cout` :

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

Pour que `cout` accepte un objet `Date` après l’opérateur d’insertion, surchargez l’opérateur d’insertion pour reconnaître un objet `ostream` à gauche et un objet `Date` à droite. La fonction d’opérateur `<<` surchargé doit ensuite être déclarée comme ami (friend) de la classe `Date` pour pouvoir accéder aux données privées dans un objet `Date`.

```cpp
// overload_date.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Date
{
    int mo, da, yr;
public:
    Date(int m, int d, int y)
    {
        mo = m; da = d; yr = y;
    }
    friend ostream& operator<<(ostream& os, const Date& dt);
};

ostream& operator<<(ostream& os, const Date& dt)
{
    os << dt.mo << '/' << dt.da << '/' << dt.yr;
    return os;
}

int main()
{
    Date dt(5, 6, 92);
    cout << dt;
}
```

```Output
5/6/92
```

## <a name="remarks"></a>Notes

L’opérateur surchargé retourne une référence à l’objet `ostream` d’origine, ce qui signifie que vous pouvez combiner des insertions :

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>Voir aussi

[Flux de sortie](../standard-library/output-streams.md)<br/>
