---
description: 'En savoir plus sur : partielle (C++/CLI et C++/CX)'
title: partiel (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: 8e6506e0ae5af40f1783241b5783228cfc919862
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173101"
---
# <a name="partial--ccli-and-ccx"></a>partiel (C++/CLI et C++/CX)

Le mot clé **partial** permet de créer indépendamment et dans différents fichiers différentes parties de la même classe ref.

## <a name="all-runtimes"></a>Tous les runtimes

(Cette fonctionnalité de langage s’applique uniquement à Windows Runtime.)

## <a name="windows-runtime"></a>Windows Runtime

Pour une classe ref qui a deux définitions partielles, le mot clé **Partial** est appliqué à la première occurrence de la définition, et cette opération est généralement effectuée par du code généré automatiquement, de sorte qu’un codeur humain n’utilise pas très souvent le mot clé. Pour toutes les définitions partielles de la classe suivantes, omettez le modificateur **partial** du mot clé *class-key* et de l’identificateur de classe. Lorsque le compilateur rencontre une classe ref et un identificateur de classe définis précédemment, mais aucun mot clé **partial**, il combine en interne toutes les parties de la définition de classe ref dans une seule définition.

### <a name="syntax"></a>Syntaxe

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>Paramètres

*class-key*<br/>
Un mot clé qui déclare une classe ou un struct pris en charge par Windows Runtime. **ref class**, **value class**, **ref struct**, ou **value struct**.

*identifier*<br/>
Le nom du type défini.

### <a name="remarks"></a>Notes

Une classe partielle prend en charge les scénarios dans lesquels vous modifiez une partie d’une définition de classe dans un fichier, et un logiciel de génération de code automatique, par exemple le concepteur XAML, modifie le code de la même classe dans un autre fichier. L’utilisation d’une classe partielle vous permet d’empêcher le générateur de code automatique de remplacer votre code. Dans un projet Visual Studio, le modificateur **partial** est appliqué automatiquement au fichier généré.

Contenu : à deux exceptions près, une définition de classe partielle peut contenir tout ce que la définition de classe complète peut contenir si le mot clé **Partial** a été omis. Toutefois, vous ne pouvez pas spécifier d’accessibilité de classe (par exemple, `public partial class X { ... };`), ou **declspec**.

Les spécificateurs d’accès utilisés dans une définition de classe partielle pour *identifier* n’affectent pas l’accessibilité par défaut dans une définition de classe partielle ou complète suivante pour *identifier*. Les définitions incluses des membres de données statiques sont autorisées.

Déclaration : une définition partielle d’un *identificateur* de classe introduit uniquement l' *identificateur* de nom, mais l' *identificateur* ne peut pas être utilisé d’une manière qui requiert une définition de classe. Le nom *identifier* ne peut pas être utilisé pour déterminer la taille d’*identifier*, ni pour utiliser une base ou un membre d’*identifier* jusqu’à ce que le compilateur rencontre la définition complète d’*identifier*.

Nombre et classement : il peut y avoir zéro ou plusieurs définitions de classes partielles pour l' *identificateur*. Chaque définition de classe partielle d’*identifier* doit précéder lexicalement la définition complète d’*identifier* (s’il existe une définition complète ; sinon, la classe ne peut pas être utilisée, sauf si elle a été déclarée avant), mais ne doit pas obligatoirement précéder les déclarations anticipées d’*identifier*. Toutes les class-keys doivent correspondre.

Définition complète : au point de la définition complète de l' *identificateur* de classe, le comportement est le même que si la définition de l' *identificateur* avait déclaré toutes les classes de base, les membres, etc. dans l’ordre dans lequel ils ont été rencontrés et définis dans les classes partielles.

Modèles : une classe partielle ne peut pas être un modèle.

Génériques : une classe partielle peut être générique si la définition complète peut être générique. Mais toutes les classes partielles et complètes doivent avoir exactement les mêmes paramètres génériques, y compris les noms de paramètres formels.

Pour plus d’informations sur l’utilisation du mot clé **partial**, consultez [Classes partielles (C++/CX)](../cppcx/partial-classes-c-cx.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Cette fonctionnalité de langage ne s’applique pas à Common Language Runtime.)

## <a name="see-also"></a>Voir aussi

[Classes partielles (C++/CX)](../cppcx/partial-classes-c-cx.md)
