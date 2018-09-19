---
title: Intitulée instructions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fd0850c12adeb6d45298445f8f739978591b133
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072106"
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

**L’instruction goto**

L’apparence d’un *identificateur* étiquette dans le programme source déclare une étiquette. Uniquement une [goto](../cpp/goto-statement-cpp.md) instruction peut transférer le contrôle à un *identificateur* étiquette. Le fragment de code suivant illustre l’utilisation de la **goto** instruction et un *identificateur* étiquette :

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

**L’instruction case**

Les étiquettes qui apparaissent après le **cas** mot clé ne peut pas apparaître à l’extérieur un **basculer** instruction. (Cette restriction s’applique également à la **par défaut** mot clé.) Le fragment de code suivant illustre l’utilisation correcte des **cas** étiquettes :

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

Les étiquettes qui apparaissent après le **cas** mot clé ne peut pas apparaître à l’extérieur un **basculer** instruction. (Cette restriction s’applique également à la **par défaut** mot clé.) Le fragment de code suivant illustre l’utilisation correcte des **cas** étiquettes :

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

L’apparence d’un *identificateur* étiquette dans le programme source déclare une étiquette. Uniquement une [goto](../cpp/goto-statement-cpp.md) instruction peut transférer le contrôle à un *identificateur* étiquette. Le fragment de code suivant illustre l’utilisation de la **goto** instruction et un *identificateur* étiquette :

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
[switch, instruction (C++)](../cpp/switch-statement-cpp.md)