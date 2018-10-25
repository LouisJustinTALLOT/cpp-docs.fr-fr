---
title: pointers_to_members | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs:
- C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c37828e88156b5be10abdf2fc41c396fdef33784
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071834"
---
# <a name="pointerstomembers"></a>pointers_to_members

**Spécifique à C++**

Spécifie si un pointeur vers un membre de classe peut être déclaré avant la définition de classe qui lui est associée et s'il sert à contrôler la taille du pointeur et le code requis pour interpréter le pointeur.

## <a name="syntax"></a>Syntaxe

```
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )
```

## <a name="remarks"></a>Notes

Vous pouvez placer un **pointers_to_members** pragma dans votre fichier source au lieu d’utiliser le [/vmx](../build/reference/vmb-vmg-representation-method.md) options du compilateur ou le [mots clé d’héritage](../cpp/inheritance-keywords.md).

Le *déclaration de pointeur* argument spécifie si vous avez déclaré un pointeur vers un membre avant ou après la définition de fonction associé. Le *déclaration de pointeur* argument est un des deux symboles suivants :

|Argument|Commentaires|
|--------------|--------------|
|*full_generality*|Génère un code sécurisé, parfois non optimal. Vous utilisez *full_generality* si n’importe quel pointeur vers un membre est déclaré avant la définition de classe associée. Cet argument utilise toujours la représentation de pointeur spécifiée par le *most-general-representation* argument. Équivaut à /vmg.|
|*best_case*|Génère un code sécurisé et optimal à l'aide de la représentation préférentielle pour tous les pointeurs vers des membres. Nécessite de définir la classe avant de déclarer un pointeur vers un membre de la classe. La valeur par défaut est *best_case*.|

Le *most-general-representation* argument spécifie la plus petite représentation de pointeur que le compilateur peut en toute sécurité utiliser pour référencer n’importe quel pointeur vers un membre d’une classe dans une unité de traduction. L’argument peut être l’un des arguments suivants :

|Argument|Commentaires|
|--------------|--------------|
|*single_inheritance*|La représentation la plus générale est la fonction pointeur vers fonction membre héritage simple. Génère une erreur si le modèle d'héritage d'une définition de classe pour laquelle un pointeur vers un membre est déclaré est de type multiple ou virtuel.|
|*multiple_inheritance*|La représentation la plus générale est la fonction pointeur vers fonction membre héritage multiple. Génère une erreur si le modèle d'héritage d'une définition de classe pour laquelle un pointeur vers un membre est déclaré est de type virtuel.|
|*virtual_inheritance*|La représentation la plus générale est la fonction pointeur vers fonction membre héritage virtuel. Ne génère jamais d'erreur. Ceci est l’argument par défaut lorsque `#pragma pointers_to_members(full_generality)` est utilisé.|

> [!CAUTION]
> Nous vous recommandons d’insérer le **pointers_to_members** pragma uniquement dans le fichier de code source que vous souhaitez affecter et uniquement après les `#include` directives. Cette pratique atténue le risque que le pragma affecte d'autres fichiers et que vous spécifiiez par erreur plusieurs définitions pour la même variable, la même fonction ou le même nom de classe.

## <a name="example"></a>Exemple

```
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

## <a name="end-c-specific"></a>FIN de la section spécifique à C++

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)