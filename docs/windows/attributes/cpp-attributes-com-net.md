---
title: Attributs de C++ pour COM et .NET | Microsoft Docs
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe6941e8809c0d735013b56d340f27302890b149
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790660"
---
# <a name="c-attributes-for-com-and-net"></a>Attributs de C++ pour COM et .NET

Microsoft définit un ensemble d’attributs C++ qui simplifient la programmation COM et le développement du common language runtime du .NET Framework. Lorsque vous incluez des attributs dans vos fichiers sources, le compilateur fonctionne avec le fournisseur DLL pour insérer du code ou de modifier le code dans les fichiers objets générés. Ces attributs facilitent la création de fichiers .idl, des interfaces, des bibliothèques de types et d’autres éléments de COM. Dans l’environnement de développement intégré (IDE), les attributs sont pris en charge par les Assistants et par la fenêtre Propriétés.

Si les attributs de faciliter le codage détaillé nécessaire pour écrire des objets COM, vous devez dans [COM fundamentals](/windows/desktop/com/the-component-object-model) mieux les utiliser.

> [!NOTE]
> Si vous cherchez des attributs standards C++, consultez [attributs](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Objectif des attributs

Attributs étendent C++ dans les directions n’est pas actuellement possibles sans casser la structure classique de la langue. Attributs permettent aux fournisseurs (DLL séparées) pour étendre les fonctionnalités de langage dynamique. Le principal objectif des attributs est de simplifier la création de composants COM, en plus d’augmenter la productivité des développeurs de composants. Attributs peuvent être appliqués à presque n’importe quelle construction C++, telles que des classes, des membres de données ou des fonctions membres. Voici une mise en surbrillance des avantages offerts par cette nouvelle technologie :

- Expose une convention d’appel familière et simple.

- Le code inséré, qui, contrairement aux macros, n’est reconnu par le débogueur.

- Permet la dérivation facile à partir de classes de base sans détails d’implémentation laborieux.

- Remplace la grande quantité de code IDL requis par un composant COM avec quelques attributs simples.

Par exemple, pour implémenter un récepteur d’événements simple pour une classe ATL générique, vous pouvez appliquer le [event_receiver](event-receiver.md) attribut sur une classe spécifique, tel que `CMyReceiver`. Le `event_receiver` attribut est ensuite compilé par le compilateur Visual C++, qui insère le code approprié dans le fichier objet.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Vous pouvez ensuite configurer le `CMyReceiver` méthodes `handler1` et `handler2` pour gérer les événements (à l’aide de la fonction intrinsèque [__hook](../../cpp/hook.md)) à partir d’une source d’événement, vous pouvez créer à l’aide de [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Mécanismes de base des attributs

Il existe trois façons d’insérer des attributs dans votre projet. Tout d’abord, vous pouvez les insérer manuellement dans votre code source. Ensuite, vous pouvez insérer à l’aide de la grille des propriétés d’un objet dans votre projet. Enfin, vous pouvez insérer à l’aide de différents Assistants. Pour plus d’informations sur l’utilisation de la **propriétés** fenêtre et les différents Assistants, consultez [création et gestion de projets Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md).

Comme précédemment, lorsque le projet est généré, le compilateur analyse chaque fichier source C++, produit un fichier objet. Toutefois, lorsque le compilateur rencontre un attribut, il est analysé et sa syntaxe est vérifiée. Le compilateur appelle ensuite dynamiquement un fournisseur d’attributs pour insérer du code ou apporter d’autres modifications à la compilation. L’implémentation du fournisseur diffère selon le type d’attribut. Par exemple, les attributs liés à ATL sont implémentés par Atlprov.dll.

La figure suivante montre la relation entre le compilateur et le fournisseur d’attributs.

![Communication des attributs de composant](../media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> L’utilisation d’attribut ne modifie pas le contenu du fichier source. Le seul moment où que le code généré d’attribut est visible est au cours de sessions de débogage. En outre, pour chaque fichier source dans le projet, vous pouvez générer un fichier texte qui affiche les résultats de la substitution de l’attribut. Pour plus d’informations sur cette procédure, consultez [/Fx (fusionner le Code injecté)](../../build/reference/fx-merge-injected-code.md) et [débogage de Code injecté](/visualstudio/debugger/how-to-debug-injected-code).

Comme la plupart des constructions C++, les attributs ont un ensemble de caractéristiques qui définit leur utilisation appropriée. Cela est appelé le contexte de l’attribut et est traité dans la table de contexte d’attribut pour chaque rubrique de référence d’attribut. Par exemple, le [coclasse](coclass.md) attribut peut uniquement être appliqué à une classe existante ou une structure, par opposition à la [cpp_quote](cpp-quote.md) attribut, qui peut être inséré n’importe où dans un fichier source C++.

## <a name="building-an-attributed-program"></a>Générer un programmes par attributs

Une fois que vous placez des attributs Visual C++ dans votre code source, vous souhaiterez peut-être le compilateur Visual C++ pour générer un fichier de bibliothèque et .idl de type pour vous. Des options de l’éditeur de liens suivant vous aident à générer des fichiers .tlb et .idl :

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Certains projets contiennent plusieurs fichiers .idl indépendants. Ceux-ci sont utilisés pour produire deux ou plusieurs fichiers .tlb et éventuellement de les lier dans le bloc de ressources. Ce scénario n’est pas pris en charge dans Visual C++.

En outre, l’éditeur de liens Visual C++ génère toutes les informations d’attributs IDL pour un seul fichier MIDL. Il n’y aura aucun moyen de générer deux bibliothèques de types à partir d’un projet unique.

## <a name="contexts"></a> Contextes d’attribut

Attributs C++ peuvent être décrits à l’aide de quatre champs de base : la cible, elles peuvent être appliquées à (**s’applique à**), si elles sont renouvelables ou non (**Repeatable**), le requis la présence d’autres attributs ( **Attributs requis**) et les incompatibilités avec d’autres attributs (**attributs non valides**). Ces champs sont répertoriés dans une table qui accompagne cet article dans la rubrique de référence de chaque attribut. Chacun de ces champs est décrite ci-dessous.
  
### <a name="applies-to"></a>S'applique à

Ce champ décrit les éléments de langage C++ différents qui sont des cibles juridiques pour l’attribut spécifié. Par exemple, si un attribut spécifie « classe » dans le **s’applique à** champ, cela indique que l’attribut peut uniquement être appliqué à une classe C++ juridique. Si l’attribut est appliqué à une fonction membre d’une classe, une erreur de syntaxe est générée.
  
Pour plus d’informations, consultez [attributs par utilisation](attributes-by-usage.md).
  
### <a name="repeatable"></a>Renouvelable

Ce champ indique si l’attribut peut être appliqué à plusieurs reprises sur la même cible. La majorité des attributs ne sont pas reproductibles.
  
### <a name="required-attributes"></a>Attributs requis

Ce champ répertorie les autres attributs qui doivent être présents (est, appliqué à la même cible) pour l’attribut spécifié fonctionner correctement. Il est rare qu’un attribut d’avoir toutes les entrées pour ce champ.
  
### <a name="invalid-attributes"></a>Attributs non valides

Ce champ répertorie les autres attributs qui ne sont pas compatibles avec l’attribut spécifié. Il est rare qu’un attribut d’avoir toutes les entrées pour ce champ.

## <a name="in-this-section"></a>Dans cette section

[Programmation par attributs (FAQ)](attribute-programming-faq.md)<br/>
[Attributs par groupe](attributes-by-group.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)<br/>
[Référence alphabétique des attributs](attributes-alphabetical-reference.md)