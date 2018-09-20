---
title: Déclaration de propriété | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 019b8eae17952bfe53fd8fbf14db4bafce1bf463
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438299"
---
# <a name="property-declaration"></a>Déclaration de propriété

La manière de déclarer une propriété dans une classe managée a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

Dans les Extensions managées de conception, chacune `set` ou `get` accesseur de propriété est spécifiée comme une méthode indépendante. La déclaration de chaque méthode est préfixée avec le `__property` mot clé. Le nom de la méthode commence par `set_` ou `get_` suivie du nom réel de la propriété (visible par l’utilisateur). Par conséquent, un `Vector` fournissant un `x` coordonner `get` propriété `get_x` et l’utilisateur peut appeler en tant que `x`. Cette convention d’affectation de noms et la spécification séparée des méthodes réellement reflète l’implémentation sous-jacente de runtime de la propriété. Par exemple, voici notre `Vector` avec un ensemble de propriétés de coordonnées :

```
public __gc __sealed class Vector {
public:
   __property double get_x(){ return _x; }
   __property double get_y(){ return _y; }
   __property double get_z(){ return _z; }

   __property void set_x( double newx ){ _x = newx; }
   __property void set_y( double newy ){ _y = newy; }
   __property void set_z( double newz ){ _z = newz; }
};
```

Cela permet de répartir les fonctionnalités associées à une propriété et oblige l’utilisateur à unifier lexicalement la Get et Set associées. En outre, il est documenté. Dans la nouvelle syntaxe, ce qui est plus similaire à celle de C#, le `property` mot clé est suivi par le type de la propriété et son nom sans ornement. Le `set` et `get` méthodes d’accès sont placées dans un bloc après le nom de propriété. Notez que contrairement à c#, la signature de la méthode d’accès est spécifiée. Par exemple, voici l’exemple de code ci-dessus traduit dans la nouvelle syntaxe.

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

      void set( double newx ) {
         _x = newx;
      }
   } // Note: no semi-colon
};
```

Si les méthodes d’accès de la propriété reflètent des niveaux d’accès distincts - comme une `public get` et un `private` ou `protected set`, une étiquette d’accès explicite peut être spécifiée. Par défaut, le niveau d’accès de la propriété reflète celle du niveau d’accès englobant. Par exemple, dans la définition ci-dessus de `Vector`, à la fois le `get` et `set` sont des méthodes `public`. Pour rendre le `set` méthode `protected` ou `private`, la définition serait modifiée comme suit :

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

   private:
      void set( double newx ) {
         _x = newx;
      }

   } // note: extent of private culminates here

// note: dot is a public method of Vector
double dot( const Vector^ wv );

// etc.
};
```

La portée d’un mot clé d’accès au sein d’une propriété s’étend jusqu'à ce que soit l’accolade fermante de la propriété ou la spécification d’un mot clé d’accès supplémentaire. Il ne s’étend pas au-delà de la définition de la propriété au niveau d’accès englobant dans lequel la propriété est définie. Dans la déclaration ci-dessus, par exemple, `Vector::dot()` est une méthode publique.

L’écriture des propriétés set/get pour les trois `Vector` coordonnées implique trois étapes :

1. Déclarez un membre de l’état privé du type approprié.

1. retourner lorsque l’utilisateur souhaite obtenir sa valeur.

1. Il attribue la nouvelle valeur.

Dans la nouvelle syntaxe, une syntaxe de propriété abrégée est disponible qui automatise ce modèle d’utilisation :

```
public ref class Vector sealed {
public:
   // equivalent shorthand property syntax
   property double x;
   property double y;
   property double z;
};
```

L’effet secondaire intéressant de la syntaxe de propriété abrégée est que bien que le membre est généré par le compilateur, il n’est pas accessible au sein de la classe, sauf via les accesseurs set/get.

## <a name="see-also"></a>Voir aussi

[Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[propriété](../windows/property-cpp-component-extensions.md)