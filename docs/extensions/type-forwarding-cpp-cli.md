---
title: Transfert de type (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: c5148c05e5580942d885b310e35f3b629224a654
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515974"
---
# <a name="type-forwarding-ccli"></a>Transfert de type (C++/CLI)

Le *transfert de type* vous permet de déplacer un type à partir d’un assembly (assembly A) dans un autre assembly (assembly B), afin qu’il ne soit pas nécessaire de recompiler les clients qui utilisent l’assembly A.

## <a name="windows-runtime"></a>Windows Runtime

Cette fonctionnalité n’est pas prise en charge dans Windows Runtime.

## <a name="common-language-runtime"></a>Common Language Runtime

L’exemple de code suivant illustre l’utilisation du transfert de type.

### <a name="syntax"></a>Syntaxe

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Paramètres

*new*<br/>
L’assembly dans lequel vous déplacez la définition de type.

*type*<br/>
Le type dont vous déplacez la définition dans un autre assembly.

### <a name="remarks"></a>Remarques

Une fois un composant (assembly) livré et utilisé par les applications clientes, vous pouvez utiliser le transfert de type pour déplacer un type depuis le composant (assembly) vers un autre assembly, fournir le composant mis à jour (et les autres assemblys requis), et les applications clientes continueront de fonctionner sans être recompilées.

Le transfert de type fonctionne uniquement pour les composants référencés par les applications existantes. Lors de la reconstruction d’une application, il doit exister des références d’assembly appropriées pour tous les types utilisés dans l’application.

Lorsque vous transférez un type (Type A) à partir d’un assembly, vous devez ajouter l’attribut `TypeForwardedTo` pour ce type, ainsi qu’une référence d’assembly. L’assembly que vous référencez doit contenir un des éléments suivants :

- La définition du Type A.

- Un attribut `TypeForwardedTo` du Type A, ainsi qu’une référence d’assembly.

Voici quelques exemples de types qui peuvent être transférés :

- les classes de référence

- les classes de valeur

- enums

- interfaces

Vous ne pouvez pas transférer les types suivants :

- Types génériques

- Types natifs

- Types imbriqués (si vous souhaitez transférer un type imbriqué, vous devez transférer le type englobant)

Vous pouvez transférer un type vers un assembly créé dans n’importe quel langage ciblant le common language runtime.

Par conséquent, si un fichier de code source qui est utilisé pour générer l’assembly A.dll contient une définition de type (`ref class MyClass`), et que vous voulez déplacer ce type de définition de l’assembly B.dll, vous le feriez pour :

1. Déplacez la définition du type `MyClass` dans un fichier de code source utilisé pour générer B.dll.

2. Générer l’assembly B.dll

3. Supprimez la définition du type `MyClass` du code source utilisé pour générer A.dll, et remplacez-la par :

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Générez l’assembly A.dll.

5. Utilisez A.dll sans recompiler les applications clientes.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`