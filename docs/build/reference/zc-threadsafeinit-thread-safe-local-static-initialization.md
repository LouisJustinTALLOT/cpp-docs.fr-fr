---
title: "/Zc:threadSafeInit (thread-safe l’initialisation statique locale) | Documents Microsoft"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a03f3ea67c9ecabd6fa68d653a3e1812fb0266cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit (thread-safe l’initialisation statique locale)  
Le `/Zc:threadSafeInit` option du compilateur indique au compilateur pour initialiser les variables locales statiques (portée de fonction) de façon thread-safe, en éliminant la nécessité pour une synchronisation manuelle. Seule l’initialisation est thread-safe. Utilisation et modification de variables locales statiques par plusieurs threads doivent toujours être synchronisés manuellement. Cette option est disponible à partir de Visual Studio 2015. Par défaut, Visual Studio active cette option.  
  
## <a name="syntax"></a>Syntaxe  
  
`/Zc:threadSafeInit`[`-`]  
  
## <a name="remarks"></a>Notes  
  
Dans la norme C ++ 11, variables de portée de bloc avec statique ou une durée de stockage thread doit être initialisée à zéro avant toute autre initialisation a lieu. L’initialisation se produit lorsque le contrôle passe tout d’abord via la déclaration de la variable. Si une exception est levée pendant l’initialisation, la variable est considérée comme non initialisé et l’initialisation est tentée de nouveau le contrôle de temps suivant passe par la déclaration. Si le contrôle passe à la déclaration en même temps que l’initialisation, les blocs de l’exécution simultanée, tandis que l’initialisation est terminée. Le comportement est indéfini si le contrôle entre la déclaration de manière récursive à nouveau lors de l’initialisation. Par défaut, Visual Studio à partir de Visual Studio 2015 implémente ce comportement par défaut. Ce comportement peut être spécifié explicitement en définissant la `/Zc:threadSafeInit` option du compilateur.  
  
L’initialisation de variables locales statiques thread-safe s’appuie sur le code implémenté dans la bibliothèque de runtime C universel (UCRT). Pour éviter de créer une dépendance sur la bibliothèque UCRT, ou pour conserver le comportement de l’initialisation du thread-safe de versions de Visual Studio antérieures à Visual Studio 2015, utilisez la `/Zc:threadSafeInit-` option. Si vous savez que la sécurité des threads n’est pas nécessaire, utilisez cette option pour générer un code légèrement plus petit et plus rapide autour des déclarations locales statiques.  
  
Les variables locales statiques thread-safe utilisent le stockage local des threads (TLS) en interne pour fournir une exécution efficace lorsque la méthode statique a déjà été initialisée. L’implémentation de cette fonctionnalité s’appuie sur les fonctions de prise en charge de système d’exploitation Windows dans Windows Vista et les systèmes d’exploitation ultérieurs. Windows XP, Windows Server 2003 et les systèmes d’exploitation plus anciens n’ont pas cette prise en charge, afin qu’ils n’obtiennent pas l’avantage de l’efficacité. Ces systèmes d’exploitation ont également une limite inférieure du nombre de sections TLS qui peut être chargé. Dépassant le TLS limite de section peut provoquer un incident. S’il s’agit d’un problème dans votre code, en particulier dans le code qui doit s’exécuter sur les systèmes d’exploitation plus anciens, utilisez `/Zc:threadSafeInit-` pour désactiver le code d’initialisation du thread-safe.  
  
Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).
2.  À partir de la **Configurations** menu déroulant, choisissez **toutes les Configurations**.
3.  Sélectionnez le **propriétés de Configuration**, **C/C++**, **ligne de commande** page de propriétés.
4.  Modifier la **des Options supplémentaires** propriété à inclure `/Zc:threadSafeInit` ou `/Zc:threadSafeInit-` , puis **OK**.

## <a name="see-also"></a>Voir aussi  
[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
[/Zc (conformité)](../../build/reference/zc-conformance.md)  
