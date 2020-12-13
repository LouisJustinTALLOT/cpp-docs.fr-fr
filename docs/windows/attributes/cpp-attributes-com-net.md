---
description: 'En savoir plus sur : attributs C++ pour COM et .NET'
title: Attributs C++ pour COM et .NET
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 6fc791f81ddc43f9f91c8ab46db6aebf1959d16b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333217"
---
# <a name="c-attributes-for-com-and-net"></a>Attributs C++ pour COM et .NET

Microsoft définit un ensemble d’attributs C++ qui simplifient la programmation COM et le développement .NET Framework common language runtime. Lorsque vous incluez des attributs dans vos fichiers sources, le compilateur utilise des dll de fournisseur pour insérer du code ou modifier le code dans les fichiers objets générés. Ces attributs facilitent la création de fichiers. idl, d’interfaces, de bibliothèques de types et d’autres éléments COM. Dans l’environnement de développement intégré (IDE), les attributs sont pris en charge par les assistants et par la Fenêtre Propriétés.

Tandis que les attributs éliminent le codage détaillé requis pour écrire des objets COM, vous avez besoin d’un arrière-plan de [principes fondamentaux de com](/windows/win32/com/the-component-object-model) pour les utiliser au mieux.

> [!NOTE]
> Si vous recherchez des attributs standard C++, consultez [attributs](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Objectif des attributs

Les attributs étendent C++ dans des directions qui ne sont actuellement pas possibles sans rompre la structure classique du langage. Les attributs permettent aux fournisseurs (dll séparées) d’étendre les fonctionnalités de langage de manière dynamique. L’objectif principal des attributs est de simplifier la création de composants COM, en plus d’augmenter le niveau de productivité du développeur de composants. Les attributs peuvent être appliqués à presque toutes les constructions C++, telles que les classes, les membres de données ou les fonctions membres. Voici une sélection des avantages offerts par cette nouvelle technologie :

- Expose une convention d’appel familière et simple.

- Utilise le code inséré, qui, contrairement aux macros, est reconnu par le débogueur.

- Permet une dérivation facile à partir des classes de base sans détails d’implémentation trop lourdes.

- Remplace la grande quantité de code IDL requise par un composant COM par quelques attributs concis.

Par exemple, pour implémenter un récepteur d’événements simple pour une classe ATL générique, vous pouvez appliquer l’attribut [event_receiver](event-receiver.md) à une classe spécifique telle que `CMyReceiver` . L' `event_receiver` attribut est ensuite compilé par le compilateur Microsoft C++, qui insère le code approprié dans le fichier objet.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Vous pouvez ensuite configurer les `CMyReceiver` méthodes `handler1` et gérer les `handler2` événements (à l’aide de la fonction intrinsèque [__hook](../../cpp/hook.md)) à partir d’une source d’événement, que vous pouvez créer à l’aide de [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Mécanismes de base des attributs

Il existe trois façons d’insérer des attributs dans votre projet. Tout d’abord, vous pouvez les insérer manuellement dans votre code source. Deuxièmement, vous pouvez les insérer à l’aide de la grille des propriétés d’un objet dans votre projet. Enfin, vous pouvez les insérer à l’aide des différents Assistants. Pour plus d’informations sur l’utilisation de la fenêtre **Propriétés** et des différents Assistants, consultez [projets Visual Studio-C++](../../build/creating-and-managing-visual-cpp-projects.md).

Comme précédemment, lorsque le projet est généré, le compilateur analyse chaque fichier source C++, en produisant un fichier objet. Toutefois, lorsque le compilateur rencontre un attribut, il est analysé et vérifié de façon syntaxique. Le compilateur appelle ensuite dynamiquement un fournisseur d’attributs pour insérer du code ou effectuer d’autres modifications au moment de la compilation. L’implémentation du fournisseur diffère selon le type d’attribut. Par exemple, les attributs associés à ATL sont implémentés par Atlprov.dll.

L’illustration suivante montre la relation entre le compilateur et le fournisseur d’attributs.

![Communication des attributs de composants](../media/vccompattrcomm.gif "Communication des attributs de composants")

> [!NOTE]
> L’utilisation des attributs ne modifie pas le contenu du fichier source. La seule fois où le code d’attribut généré est visible pendant les sessions de débogage. En outre, pour chaque fichier source du projet, vous pouvez générer un fichier texte qui affiche les résultats de la substitution d’attribut. Pour plus d’informations sur cette procédure, consultez [/FX (fusionner le code injecté)](../../build/reference/fx-merge-injected-code.md) et [débogage du code injecté](/visualstudio/debugger/how-to-debug-injected-code).

Comme la plupart des constructions C++, les attributs ont un ensemble de caractéristiques qui définissent leur utilisation appropriée. C’est ce que l’on appelle le contexte de l’attribut et est traité dans la table de contexte d’attribut pour chaque rubrique de référence d’attribut. Par exemple, l’attribut [coclass](coclass.md) ne peut être appliqué qu’à une classe ou une structure existante, par opposition à l’attribut [cpp_quote](cpp-quote.md) , qui peut être inséré n’importe où dans un fichier source C++.

## <a name="building-an-attributed-program"></a>Générer un programmes par attributs

Après avoir placé Visual C++ attributs dans votre code source, vous souhaiterez peut-être que le compilateur Microsoft C++ produise une bibliothèque de types et un fichier. idl. Les options suivantes de l’éditeur de liens vous aident à générer des fichiers. tlb et. idl :

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Certains projets contiennent plusieurs fichiers. idl indépendants. Ils sont utilisés pour produire deux ou plusieurs fichiers. tlb et les lier éventuellement dans le bloc de ressources. Ce scénario n’est actuellement pas pris en charge dans Visual C++.

En outre, l’éditeur de liens Visual C++ génère toutes les informations d’attribut relatives à IDL dans un fichier MIDL unique. Il n’existe aucun moyen de générer deux bibliothèques de types à partir d’un seul projet.

## <a name="attribute-contexts"></a><a name="contexts"></a> Contextes d’attribut

Les attributs C++ peuvent être décrits à l’aide de quatre champs de base : la cible à laquelle ils peuvent être appliqués (**s’applique à**), s’ils sont reproductibles ou non (**reproductibles**), la présence requise d’autres attributs (**attributs requis**) et des incompatibilités avec d’autres attributs (**attributs non valides**). Ces champs sont répertoriés dans une table associée dans la rubrique de référence de chaque attribut. Chacun de ces champs est décrit ci-dessous.

### <a name="applies-to"></a>S'applique à

Ce champ décrit les différents éléments du langage C++ qui sont des cibles juridiques pour l’attribut spécifié. Par exemple, si un attribut spécifie « Class » dans le champ **s’applique à** , cela indique que l’attribut ne peut être appliqué qu’à une classe C++ légale. Si l’attribut est appliqué à une fonction membre d’une classe, une erreur de syntaxe se produit.

Pour plus d’informations, consultez [attributs par utilisation](attributes-by-usage.md).

### <a name="repeatable"></a>Renouvelable

Ce champ indique si l’attribut peut être appliqué à plusieurs reprises à la même cible. La majorité des attributs ne sont pas reproductibles.

### <a name="required-attributes"></a>Attributs requis

Ce champ répertorie les autres attributs qui doivent être présents (c’est-à-dire appliqués à la même cible) pour que l’attribut spécifié fonctionne correctement. Il est rare qu’un attribut ait des entrées pour ce champ.

### <a name="invalid-attributes"></a>Attributs non valides

Ce champ répertorie les autres attributs incompatibles avec l’attribut spécifié. Il est rare qu’un attribut ait des entrées pour ce champ.

## <a name="in-this-section"></a>Dans cette section

[FAQ sur la programmation des attributs](attribute-programming-faq.md)<br/>
[Attributs par groupe](attributes-by-group.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)<br/>
[Référence alphabétique des attributs](attributes-alphabetical-reference.md)
