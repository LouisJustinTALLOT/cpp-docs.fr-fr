---
description: 'En savoir plus sur les éléments suivants : constructeurs de déplacement et opérateurs d’assignation de déplacement (C++)'
title: 'Comment : définir des constructeurs de déplacement et des opérateurs d’assignation de déplacement (C++)'
ms.date: 03/05/2018
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
ms.openlocfilehash: 9430f4970a0f911000c31b142ed177aee7dff2d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313968"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Constructeurs de déplacement et opérateurs d'assignation de déplacement (C++)

Cette rubrique explique comment écrire un *constructeur de déplacement* et un opérateur d’assignation de déplacement pour une classe C++. Un constructeur de déplacement permet de déplacer les ressources détenues par un objet rvalue dans une lvalue sans la copier. Pour plus d’informations sur la sémantique de déplacement, consultez [déclarateur de référence rvalue :  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

Cette rubrique repose sur la classe C++ suivante, `MemoryBlock`, qui gère une mémoire tampon.

```cpp
// MemoryBlock.h
#pragma once
#include <iostream>
#include <algorithm>

class MemoryBlock
{
public:

   // Simple constructor that initializes the resource.
   explicit MemoryBlock(size_t length)
      : _length(length)
      , _data(new int[length])
   {
      std::cout << "In MemoryBlock(size_t). length = "
                << _length << "." << std::endl;
   }

   // Destructor.
   ~MemoryBlock()
   {
      std::cout << "In ~MemoryBlock(). length = "
                << _length << ".";

      if (_data != nullptr)
      {
         std::cout << " Deleting resource.";
         // Delete the resource.
         delete[] _data;
      }

      std::cout << std::endl;
   }

   // Copy constructor.
   MemoryBlock(const MemoryBlock& other)
      : _length(other._length)
      , _data(new int[other._length])
   {
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      std::copy(other._data, other._data + _length, _data);
   }

   // Copy assignment operator.
   MemoryBlock& operator=(const MemoryBlock& other)
   {
      std::cout << "In operator=(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      if (this != &other)
      {
         // Free the existing resource.
         delete[] _data;

         _length = other._length;
         _data = new int[_length];
         std::copy(other._data, other._data + _length, _data);
      }
      return *this;
   }

   // Retrieves the length of the data resource.
   size_t Length() const
   {
      return _length;
   }

private:
   size_t _length; // The length of the resource.
   int* _data; // The resource.
};
```

Les procédures suivantes décrivent comment écrire un constructeur de déplacement ou un opérateur d'assignation de déplacement pour l'exemple de classe C++.

### <a name="to-create-a-move-constructor-for-a-c-class"></a>Pour créer un constructeur de déplacement pour une classe C++

1. Définissez une méthode de constructeur vide qui accepte une référence rvalue au type de classe comme paramètre, comme illustré dans l'exemple suivant :

    ```cpp
    MemoryBlock(MemoryBlock&& other)
       : _data(nullptr)
       , _length(0)
    {
    }
    ```

1. Dans le constructeur de déplacement, assignez les données membres de classe de l'objet source à l'objet en cours de construction :

    ```cpp
    _data = other._data;
    _length = other._length;
    ```

1. Assignez les données membres de l'objet source aux valeurs par défaut. Cela empêche le destructeur de libérer des ressources (telles que de la mémoire) à plusieurs reprises :

    ```cpp
    other._data = nullptr;
    other._length = 0;
    ```

### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>Pour créer un opérateur d'assignation de déplacement pour une classe C++

1. Définissez un opérateur d'assignation vide qui accepte une référence rvalue au type de classe comme paramètre et retourne une référence au type de classe, comme illustré dans l'exemple suivant :

    ```cpp
    MemoryBlock& operator=(MemoryBlock&& other)
    {
    }
    ```

1. Dans l'opérateur d'assignation de déplacement, ajoutez une instruction conditionnelle qui n'effectue aucune opération si vous essayez d'assigner l'objet à lui-même.

    ```cpp
    if (this != &other)
    {
    }
    ```

1. Dans l'instruction conditionnelle, libérez des ressources (telles que de la mémoire) à partir de l'objet auquel elles sont assignées.

   L'exemple suivant libère le membre `_data` de l'objet auquel il est assigné :

    ```cpp
    // Free the existing resource.
    delete[] _data;
    ```

   Suivez les étapes 2 et 3 de la première procédure pour transférer les données membres de l'objet source vers l'objet en cours de construction :

    ```cpp
    // Copy the data pointer and its length from the
    // source object.
    _data = other._data;
    _length = other._length;

    // Release the data pointer from the source object so that
    // the destructor does not free the memory multiple times.
    other._data = nullptr;
    other._length = 0;
    ```

1. Retournez une référence à l'objet actif, comme indiqué dans l'exemple suivant :

    ```cpp
    return *this;
    ```

## <a name="example-complete-move-constructor-and-assignment-operator"></a>Exemple : terminer le constructeur de déplacement et l’opérateur d’assignation

L'exemple suivant montre le constructeur de déplacement et l'opérateur d'assignation de déplacement complets pour la classe `MemoryBlock` :

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other) noexcept
   : _data(nullptr)
   , _length(0)
{
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "
             << other._length << ". Moving resource." << std::endl;

   // Copy the data pointer and its length from the
   // source object.
   _data = other._data;
   _length = other._length;

   // Release the data pointer from the source object so that
   // the destructor does not free the memory multiple times.
   other._data = nullptr;
   other._length = 0;
}

// Move assignment operator.
MemoryBlock& operator=(MemoryBlock&& other) noexcept
{
   std::cout << "In operator=(MemoryBlock&&). length = "
             << other._length << "." << std::endl;

   if (this != &other)
   {
      // Free the existing resource.
      delete[] _data;

      // Copy the data pointer and its length from the
      // source object.
      _data = other._data;
      _length = other._length;

      // Release the data pointer from the source object so that
      // the destructor does not free the memory multiple times.
      other._data = nullptr;
      other._length = 0;
   }
   return *this;
}
```

## <a name="example-use-move-semantics-to-improve-performance"></a>Exemple d’utilisation de la sémantique de déplacement pour améliorer les performances

L'exemple suivant montre comment la sémantique de déplacement peut améliorer les performances de vos applications. L'exemple ajoute deux éléments à un objet vectoriel, puis insère un nouvel élément entre les deux éléments existants. La `vector` classe utilise la sémantique de déplacement pour exécuter efficacement l’opération d’insertion en déplaçant les éléments du vecteur au lieu de les copier.

```cpp
// rvalue-references-move-semantics.cpp
// compile with: /EHsc
#include "MemoryBlock.h"
#include <vector>

using namespace std;

int main()
{
   // Create a vector object and add a few elements to it.
   vector<MemoryBlock> v;
   v.push_back(MemoryBlock(25));
   v.push_back(MemoryBlock(75));

   // Insert a new element into the second position of the vector.
   v.insert(v.begin() + 1, MemoryBlock(50));
}
```

Cet exemple produit la sortie suivante :

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Avant Visual Studio 2010, cet exemple produisait la sortie suivante :

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.
In ~MemoryBlock(). length = 75. Deleting resource.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In operator=(const MemoryBlock&). length = 75. Copying resource.
In operator=(const MemoryBlock&). length = 50. Copying resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

La version de cet exemple qui utilise la sémantique de déplacement est plus efficace que celle qui ne l'utilise pas, car elle exécute moins d'opérations de copie, d'allocation de mémoire et de libération de mémoire.

## <a name="robust-programming"></a>Programmation fiable

Pour éviter les fuites de ressources, libérez toujours des ressources (telles que la mémoire, les handles de fichiers et les sockets) dans l'opérateur d'assignation de déplacement.

Pour empêcher la destruction irrécupérable des ressources, gérez correctement l'auto-assignation dans l'opérateur d'assignation de déplacement.

Si vous fournissez un constructeur de déplacement et un opérateur d'assignation de déplacement pour votre classe, vous pouvez supprimer le code redondant en écrivant le constructeur de déplacement de sorte qu'il appelle l'opérateur d'assignation de déplacement. L'exemple suivant présente une version modifiée du constructeur de déplacement qui appelle l'opérateur d'assignation de déplacement :

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other) noexcept
   : _data(nullptr)
   , _length(0)
{
   *this = std::move(other);
}
```

La fonction [std :: Move](../standard-library/utility-functions.md#move) convertit la lvalue `other` en valeur Rvalue.

## <a name="see-also"></a>Voir aussi

[Déclarateur de référence Rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
[std :: Move](../standard-library/utility-functions.md#move)
