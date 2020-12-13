---
description: 'En savoir plus sur : instructions étiquetées'
title: Instructions étiquetées
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: dcedce1e67c712102be2d8ebb697c1839f3f53c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333971"
---
# <a name="labeled-statements"></a>Instructions étiquetées

Les étiquettes sont utilisées pour transférer le contrôle du programme directement à l'instruction spécifiée.

```
identifier :  statement
case constant-expression :  statement
default :  statement
```

La portée d'une étiquette est la fonction entière dans laquelle elle est déclarée.

## <a name="remarks"></a>Notes

Il existe trois types d'instructions étiquetées. Tous utilisent un deux-points pour séparer un certain type d'étiquette de l'instruction. Le cas et les étiquettes par défaut sont propres aux instructions case.

```cpp
#include <iostream>
using namespace std;

void test_label(int x) {

    if (x == 1){
        goto label1;
    }
    goto label2;

label1:
    cout << "in label1" << endl;
    return;

label2:
    cout << "in label2" << endl;
    return;
}

int main() {
    test_label(1);  // in label1
    test_label(2);  // in label2
}
```

**Instruction goto**

L’apparence d’une étiquette d' *identificateur* dans le programme source déclare une étiquette. Seule une instruction [goto](../cpp/goto-statement-cpp.md) peut transférer le contrôle à une étiquette d' *identificateur* . Le fragment de code suivant illustre l’utilisation de l' **`goto`** instruction et d’une étiquette d' *identificateur* :

Une étiquette ne peut pas apparaître seule, mais doit toujours être attachée à une instruction. Si une étiquette doit apparaître seule, placez une instruction null après l'étiquette.

L'étiquette a une portée de fonction et ne peut pas être redéclarée dans la fonction. Toutefois, le même nom peut être utilisé en tant qu'étiquette dans différentes fonctions.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
}

//Output: At Test2 label.
```

**Instruction case**

Les étiquettes qui s’affichent après le **`case`** mot clé ne peuvent pas également apparaître en dehors d’une **`switch`** instruction. (Cette restriction s’applique également au **`default`** mot clé.) Le fragment de code suivant illustre l’utilisation correcte des **`case`** étiquettes :

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );
      EndPaint( hWnd, &ps );
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-case-statement"></a>Étiquettes dans l'instruction case

Les étiquettes qui s’affichent après le **`case`** mot clé ne peuvent pas également apparaître en dehors d’une **`switch`** instruction. (Cette restriction s’applique également au **`default`** mot clé.) Le fragment de code suivant illustre l’utilisation correcte des **`case`** étiquettes :

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      // Obtain a handle to the device context.
      // BeginPaint will send WM_ERASEBKGND if appropriate.

      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );

      // Inform Windows that painting is complete.

      EndPaint( hWnd, &ps );
      break;

   case WM_CLOSE:
      // Close this window and all child windows.

      KillTimer( hWnd, TIMER1 );
      DestroyWindow( hWnd );
      if ( hWnd == hWndMain )
         PostQuitMessage( 0 );  // Quit the application.
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-goto-statement"></a>Étiquettes dans l'instruction goto

L’apparence d’une étiquette d' *identificateur* dans le programme source déclare une étiquette. Seule une instruction [goto](../cpp/goto-statement-cpp.md) peut transférer le contrôle à une étiquette d' *identificateur* . Le fragment de code suivant illustre l’utilisation de l' **`goto`** instruction et d’une étiquette d' *identificateur* :

Une étiquette ne peut pas apparaître seule, mais doit toujours être attachée à une instruction. Si une étiquette doit apparaître seule, placez une instruction null après l'étiquette.

L'étiquette a une portée de fonction et ne peut pas être redéclarée dans la fonction. Toutefois, le même nom peut être utilisé en tant qu'étiquette dans différentes fonctions.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
// At Test2 label.
}
```

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des instructions C++](../cpp/overview-of-cpp-statements.md)<br/>
[Switch, instruction (C++)](../cpp/switch-statement-cpp.md)
