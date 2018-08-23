---
title: partial (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92fd30b0b420080d33f9938bec4891ac80ac660d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597076"
---
# <a name="partial--c-component-extensions"></a>partial (extensions de composant C++)

Le **partielle** mot clé permettent aux différentes parties de la même classe ref pour être créé indépendamment et dans différents fichiers.

## <a name="all-runtimes"></a>Tous les runtimes

(Cette fonctionnalité de langage s’applique uniquement à l’exécution de Windows).

## <a name="windows-runtime"></a>Windows Runtime

Pour une classe ref qui a deux définitions partielles, le **partielle** mot clé est appliquée à la première occurrence de la définition, et il vise généralement par le code généré automatiquement, afin qu’un codeur humain n’utilise pas le mot clé très souvent. Pour toutes les définitions partielles suivantes de la classe, omettez la **partielle** modificateur à partir de la *clé-classe* mot clé et la classe de l’identificateur. Lorsque le compilateur rencontre une classe ref prédéfinie et d’identificateur de classe, mais aucune **partielle** mot clé, il combine toutes les parties de la définition de classe ref dans une seule définition.

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

*clé de classe*  
Un mot clé qui déclare une classe ou un struct qui est pris en charge par le Runtime de Windows. Soit **classe ref**, **classe value**, **ref struct**, ou **struct value**.

*identifier*  
Le nom du type défini.

### <a name="remarks"></a>Notes

Une classe partielle prend en charge les scénarios où vous modifiez une partie d’une définition de classe dans un fichier et un logiciel de génération de code automatique, par exemple, le concepteur XAML, modifie le code dans la même classe dans un autre fichier. En utilisant une classe partielle, vous pouvez empêcher le Générateur de code automatique de remplacer votre code. Dans un projet Visual Studio, le **partielle** modificateur est appliqué automatiquement au fichier généré.

Contenu : À deux exceptions près, une définition de classe partielle peut contenir tout ce que la définition de classe complète peut contenir si le **partielle** mot clé a été omis. Toutefois, vous ne pouvez pas spécifier l’accessibilité de classe (par exemple, `public partial class X { ... };`), ou un **declspec**.

Utilisé dans une définition de classe partielle pour des spécificateurs d’accès *identificateur* n’affectent pas l’accessibilité par défaut dans une définition de classe partielle ou complète suivante pour *identificateur*. Les définitions inline des données membres statiques sont autorisées.

Déclaration : Une définition partielle d’une classe *identificateur* présente uniquement le nom *identificateur*, mais *identificateur* ne peut pas être utilisé d’une manière qui requiert une classe définition. Le nom *identificateur* ne peut pas être utilisé pour déterminer la taille de *identificateur*, ou utiliser une base ni un membre de *identificateur* jusqu'à ce qu’une fois que le compilateur rencontre la définition complète de *identificateur*.

Nombre et l’ordre : il peut y avoir zéro ou plusieurs définitions de classe partielle pour *identificateur*. Chaque définition de classe partielle de *identificateur* doit précéder lexicalement la seule définition complète de *identificateur* (s’il existe une définition complète ; sinon, la classe ne peut pas être utilisée à l’exception comme si déclaré avant), mais devez faites pas précéder les déclarations anticipées de *identificateur*. Toutes les classes-clés doivent correspondre.

Complète la définition : au moment de la définition complète de la classe *identificateur*, le comportement est le même que si la définition de *identificateur* avait déclaré toutes les classes de base, les membres, etc., dans l’ordre dans lequel ils ont été rencontrés et définis dans les classes partielles.

Modèles : Une classe partielle ne peut pas être un modèle.

Les génériques : Une classe partielle peut être un générique si la définition complète peut être générique. Mais toutes les classes partielles et complètes doivent avoir exactement les mêmes paramètres génériques, y compris les noms de paramètres formels.

Pour plus d’informations sur l’utilisation de la **partielle** mot clé, consultez [des Classes partielles (C++ / c++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Cette fonctionnalité de langage ne s’applique pas pour le Common Language Runtime).

## <a name="see-also"></a>Voir aussi

[Classes partielles (C++ / c++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)