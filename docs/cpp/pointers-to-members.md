---
title: Pointeurs vers membres
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: adffacc3ddc08679d7db4e17e027d8a7dbe8a92b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320319"
---
# <a name="pointers-to-members"></a>Pointeurs vers membres

Les déclarations de pointeurs vers des membres sont des cas spéciaux de déclarations de pointeur.  Ils sont déclarés à l’aide de la séquence suivante :

> *storage-class-specifiers*<sub>opt</sub> *cv-qualifiers*<sub>opt</sub> *type-specifier* *ms-modificateur*<sub>opt</sub> *qualified-name* **`::*`** *cv-qualifiers*<sub>opt</sub> *identifier* *pm-initializer*<sub>opt</sub>**`;`**

1. Spécificateur de déclaration :

   - Spécificateur de classe de stockage facultatif.

   - Cône **const** facultatif et spécificateurs **volatils.**

   - Spécificateur de type : nom d'un type. C’est le genre de membre à souligner, pas la classe.

1. Déclarateur :

   - Modificateur spécifique à Microsoft facultatif. Pour plus d’informations, voir [Microsoft-Specific Modificateurs](../cpp/microsoft-specific-modifiers.md).

   - Nom qualifié de la classe contenant les membres vers lesquels pointer.

   - L’opérateur. __`::`__

   - L’opérateur. __`*`__

   - Cône **const** facultatif et spécificateurs **volatils.**

   - Identificateur nommant le pointeur vers le membre.

1. Un initialisateur optionnel point-à-membre :

   - L’opérateur. **`=`**

   - L’opérateur. **`&`**

   - Nom qualifié de la classe.

   - L’opérateur. __`::`__

   - Le nom d’un membre non statique de la classe du type approprié.

Comme toujours, les déclarateurs multiples (et tout initialiseur associé) sont autorisés dans une même déclaration. Un pointeur au membre ne peut pas indiquer un membre statique **`void`** de la classe, un membre de type de référence, ou .

Un pointeur pour un membre d’une classe diffère d’un pointeur normal: il a à la fois des informations de type pour le type du membre et pour la classe à laquelle le membre appartient. Un pointeur normal identifie (a l'adresse de) un seul objet en mémoire. Un pointeur vers un membre d'une classe identifie ce membre dans toute instance de la classe. L'exemple suivant déclare une classe, `Window`, et certains pointeurs vers des données membres.

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

Dans l’exemple `pwCaption` précédent, est un `Window` pointeur à `char*`tout membre de la classe qui est de type . Le type de `pwCaption` est `char * Window::*`. Le fragment de code suivant déclare des pointeurs vers les fonctions membres `SetCaption` et `GetCaption`.

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

Les pointeurs `pfnwGC` et `pfnwSC` pointent respectivement vers `GetCaption` et `SetCaption` de la classe `Window`. Le code copie directement des informations vers le titre de la fenêtre à l'aide du pointeur vers le membre `pwCaption` :

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

La différence **`.*`** entre **`->*`** les opérateurs et les opérateurs (les **`.*`** opérateurs pointeurs à membres) est **`->*`** que l’opérateur sélectionne les membres qui reçoivent une référence d’objet ou d’objet, tandis que l’opérateur sélectionne les membres par l’intermédiaire d’un pointeur. Pour plus d’informations sur ces opérateurs, voir [Expressions avec des opérateurs pointeurs à membres](../cpp/pointer-to-member-operators-dot-star-and-star.md).

Le résultat des opérateurs pointeurs à membres est le type de membre. Dans ce cas, il s’agit de `char *`.

Le fragment de code suivant appelle les fonctions membres `GetCaption` et `SetCaption` à l'aide de pointeurs vers des membres :

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>Restrictions sur les pointeurs vers des membres

L’adresse d’un membre statique n’est pas un pointeur pour un membre. C’est un pointeur régulier à l’un des cas du membre statique. Une seule instance d’un membre statique existe pour tous les objets d’une classe donnée. Cela signifie que vous pouvez utiliser**&** l’adresse ordinaire<strong>\*</strong>( ) et la déreférence ( ) les opérateurs.

## <a name="pointers-to-members-and-virtual-functions"></a>Pointeurs vers des membres et des fonctions virtuelles

Invoquer une fonction virtuelle par le biais d’une fonction pointeur-à-membre fonctionne comme si la fonction avait été appelée directement. La fonction correcte est regardée dans la table en v et invoquée.

La clé du bon fonctionnement des fonctions virtuelles est, comme toujours, de les appeler via un pointeur vers une classe de base. (Pour plus d’informations sur les fonctions virtuelles, voir [fonctions virtuelles](../cpp/virtual-functions.md).)

Le code suivant montre comment appeler une fonction virtuelle via un pointeur de fonction membre :

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
    public:
    virtual void Print();
};
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

//Output: Print function for class Base
Print function for class Derived
```
