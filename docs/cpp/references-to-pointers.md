---
title: Références aux pointeurs
ms.date: 08/20/2018
helpviewer_keywords:
- references, to pointers
ms.assetid: 4ce48b08-1511-4d2f-a31f-95f99eac0c70
ms.openlocfilehash: 060bbaef74c934de4d8529b3ceafc61d1b70dc70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512721"
---
# <a name="references-to-pointers"></a>Références aux pointeurs

Les références aux pointeurs peuvent être déclarées à peu près de la même façon que les références aux objets. La déclaration d'une référence à un pointeur produit une valeur modifiable utilisée comme un pointeur normal.

## <a name="example"></a>Exemple

Les exemples de code suivants illustrent la différence entre l'utilisation d'un pointeur vers un pointeur et d'une référence vers un pointeur.

Les fonctions `Add1` et `Add2` sont équivalentes (bien qu'elles ne soient pas appelées de la même façon). La différence est que `Add1` utilise une double indirection tandis que `Add2` utilise la présence d'une référence à un pointeur.

```cpp
// references_to_pointers.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library namespace
using namespace std;

enum {
   sizeOfBuffer = 132
};

// Define a binary tree structure.
struct BTree {
   char  *szText;
   BTree *Left;
   BTree *Right;
};

// Define a pointer to the root of the tree.
BTree *btRoot = 0;

int Add1( BTree **Root, char *szToAdd );
int Add2( BTree*& Root, char *szToAdd );
void PrintTree( BTree* btRoot );

int main( int argc, char *argv[] ) {
   // Usage message
   if( argc < 2 ) {
      cerr << "Usage: Refptr [1 | 2]" << "\n";
      cerr << "\nwhere:\n";
      cerr << "1 uses double indirection\n";
      cerr << "2 uses a reference to a pointer.\n";
      cerr << "\nInput is from stdin.\n";
      return 1;
   }

   char *szBuf = new char[sizeOfBuffer];
   if (szBuf == NULL) {
      cerr << "Out of memory!\n";
      return -1;
   }

   // Read a text file from the standard input device and
   //  build a binary tree.
   while( !cin.eof() )
   {
      cin.get( szBuf, sizeOfBuffer, '\n' );
      cin.get();

      if ( strlen( szBuf ) ) {
         switch ( *argv[1] ) {
            // Method 1: Use double indirection.
            case '1':
               Add1( &btRoot, szBuf );
               break;
            // Method 2: Use reference to a pointer.
            case '2':
               Add2( btRoot, szBuf );
               break;
            default:
               cerr << "Illegal value '"
                  << *argv[1]
                  << "' supplied for add method.\n"
                     << "Choose 1 or 2.\n";
               return -1;
         }
      }
   }
   // Display the sorted list.
   PrintTree( btRoot );
}

// PrintTree: Display the binary tree in order.
void PrintTree( BTree* MybtRoot ) {
   // Traverse the left branch of the tree recursively.
   if ( btRoot->Left )
      PrintTree( btRoot->Left );

   // Print the current node.
   cout << btRoot->szText << "\n";

   // Traverse the right branch of the tree recursively.
   if ( btRoot->Right )
      PrintTree( btRoot->Right );
}

// Add1: Add a node to the binary tree.
//       Uses double indirection.
int Add1( BTree **Root, char *szToAdd ) {
   if ( (*Root) == 0 ) {
      (*Root) = new BTree;
      (*Root)->Left = 0;
      (*Root)->Right = 0;
      (*Root)->szText = new char[strlen( szToAdd ) + 1];
      strcpy_s((*Root)->szText, (strlen( szToAdd ) + 1), szToAdd );
      return 1;
   }
   else {
      if ( strcmp( (*Root)->szText, szToAdd ) > 0 )
         return Add1( &((*Root)->Left), szToAdd );
      else
         return Add1( &((*Root)->Right), szToAdd );
   }
}

// Add2: Add a node to the binary tree.
//       Uses reference to pointer
int Add2( BTree*& Root, char *szToAdd ) {
   if ( Root == 0 ) {
      Root = new BTree;
      Root->Left = 0;
      Root->Right = 0;
      Root->szText = new char[strlen( szToAdd ) + 1];
      strcpy_s( Root->szText, (strlen( szToAdd ) + 1), szToAdd );
      return 1;
   }
   else {
      if ( strcmp( Root->szText, szToAdd ) > 0 )
         return Add2( Root->Left, szToAdd );
      else
         return Add2( Root->Right, szToAdd );
   }
}
```

```Output
Usage: Refptr [1 | 2]

where:
1 uses double indirection
2 uses a reference to a pointer.

Input is from stdin.
```

## <a name="see-also"></a>Voir aussi

[Références](../cpp/references-cpp.md)