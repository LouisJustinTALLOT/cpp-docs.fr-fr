---
title: Déclaration de propriété d’Index | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6917742b285b3700548b54fef164d01c0594e5e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380463"
---
# <a name="property-index-declaration"></a>Déclaration de l'index de la propriété

La syntaxe pour déclarer une propriété indexée a changé d’Extensions managées pour C++ vers Visual C++.

Les deux le problème principal de la prise en charge du langage des Extensions managées des propriétés indexées est l’incapacité de fournir la mise en indice de niveau classe ; Autrement dit, toutes les propriétés indexées sont requises pour se voir attribuer un nom et par conséquent, il n’existe aucun moyen, par exemple, pour fournir un opérateur d’indice managé qui peut être appliqué directement à un `Vector` ou `Matrix` objet de classe. Une seconde moins problématique est qu’il est visuellement difficile de distinguer une propriété d’une propriété indexée : le nombre de paramètres est la seule indication. Enfin, les propriétés indexées souffrent des mêmes problèmes que ceux des propriétés non indexées - les accesseurs ne sont pas traités comme une unité atomique, mais séparés dans des méthodes individuelles.  Exemple :

```
public __gc class Vector;
public __gc class Matrix {
   float mat[,];

public:
   __property void set_Item( int r, int c, float value);
   __property float get_Item( int r, int c );

   __property void set_Row( int r, Vector* value );
   __property Vector* get_Row( int r );
};
```

Comme vous pouvez le voir, les indexeurs sont distinguent uniquement par les paramètres supplémentaires pour spécifier une de deux ou unique index de dimension. Dans la nouvelle syntaxe, les indexeurs sont distinguent par le crochet ([,]) après le nom de l’indexeur et en indiquant le nombre et le type de chaque index :

```
public ref class Vector {};
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   property float Item [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

Pour indiquer un indexeur de niveau classe qui peut être appliqué directement à des objets de la classe dans la nouvelle syntaxe, le `default` mot clé est réutilisé pour se substituer à un nom explicite. Exemple :

```
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   // ok: class level indexer now
   //
   //     Matrix mat;
   //     mat[ 0, 0 ] = 1;
   //
   // invokes the set accessor of the default indexer

   property float default [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

Dans la nouvelle syntaxe, lorsque la valeur par défaut indexé propriété est spécifiée, les deux noms suivants sont réservés : `get_Item` et `set_Item`. Il s’agit, car ce sont les noms sous-jacent générés pour la propriété indexée par défaut.

Notez qu’il n’existe aucune syntaxe index simple analogue à la syntaxe de propriété simple.

## <a name="see-also"></a>Voir aussi

[Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
