---
title: Mots clés de langage (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 241205ad25314034d8d36fa7ad1b156b13080fd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134411"
---
# <a name="language-keywords-ccli"></a>Mots clés de langage (C++/CLI)
Plusieurs mots clés de langage changés entre les Extensions managées pour C++ vers Visual C++.  
  
 Dans la nouvelle syntaxe Visual C++, le trait de soulignement double est supprimé comme préfixe de tous les mots clés (avec une exception près : `__identifier` est conservé). Par exemple, une propriété est désormais déclarée en tant que `property`, et non `__property`.  
  
 Il existait deux raisons principales pour utiliser le préfixe de trait de soulignement double dans les Extensions managées :  
  
-   Il s’agit de la méthode conforme de fournir des extensions locales à la norme ISO-C++. Des principaux objectifs de la conception des Extensions managées était ne pas introduire d’incompatibilités avec le langage standard, tels que les nouveaux mots clés et des jetons. Il était donc en grande partie, qui ont motivé le choix de la syntaxe de pointeur de la déclaration d’objets des types de référence managée.  
  
-   L’utilisation d’un trait de soulignement double, en dehors de sa conformité, est également une garantie raisonnable de non invasif de la base de code existante des utilisateurs du langage. Il s’agissait d’un deuxième objectif principal de la conception des Extensions managées.  
  
 En dépit de supprimez les traits de soulignement doubles, Microsoft s’engage à être conforme. Toutefois, la prise en charge pour le modèle d’objet dynamique CLR représente un paradigme de programmation nouveau et puissant. Prise en charge de ce nouveau paradigme requiert ses propres mots clés de niveau supérieur et les jetons. Nous avons recherché fournir une expression de première classe de ce nouveau paradigme lors de l’intégration et prendre en charge le langage standard. La nouvelle conception de syntaxe fournit une expérience de programmation de première classe de ces deux modèles d’objets disparates.  
  
 De même, nous concernent la nature non invasif de ces nouveaux mots clés de langage. Cette opération a été effectuée avec l’utilisation de mots clés contextuels et espacés. Avant d’examiner la nouvelle syntaxe du langage réel, essayons sens de ces deux versions de mot clé spécial.  
  
 Un mot clé contextuel a une signification spéciale dans des contextes de programme spécifique. Dans le programme général, par exemple, `sealed` est traité comme un identificateur ordinaire. Toutefois, lorsqu’il se produit dans la partie de la déclaration d’un type de classe de référence managée, il est traité comme un mot clé dans le contexte de cette déclaration de classe. Cela réduit l’impact potentiel invasif d’introduire un nouveau mot clé dans le langage, quelque chose que nous estimons est très importante pour les utilisateurs avec une base de code existante. En même temps, il permet aux utilisateurs de la nouvelle fonctionnalité de bénéficier d’une expérience de première classe de la fonctionnalité de langage supplémentaire - quelque chose qui n’était pas possible avec les Extensions managées. Pour obtenir un exemple de procédure `sealed` sert consultez [déclaration d’un Type de classe gérée](../dotnet/declaration-of-a-managed-class-type.md).  
  
 Un mot clé espacé, tel que `value class`, est un cas spécial d’un mot clé contextuel. Il associe un mot clé existant avec un modificateur contextuel séparé par un espace. La paire est traitée comme une unité unique plutôt que comme deux mots clés distincts.  
  
## <a name="see-also"></a>Voir aussi  
 [C + c++ / CLI Initiation à la Migration](../dotnet/cpp-cli-migration-primer.md)   
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)