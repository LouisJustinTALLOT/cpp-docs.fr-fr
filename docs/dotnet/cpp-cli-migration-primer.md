---
title: C + c++ / CLI Migration Primer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: add55156b23dd2f9eb746f032d8406bad3b9db56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108684"
---
# <a name="ccli-migration-primer"></a>Initiation à la migration de C++/CLI
Il s’agit d’un repère de déplacement de vos programmes Visual C++ à partir des Extensions managées pour C++ vers Visual C++. 
  
 C + c++ / CLI étend un paradigme de programmation dynamique composant au langage standard ISO-C++. Le nouveau langage offre plusieurs améliorations significatives sur les Extensions managées. Cette section fournit une énumération des Extensions managées pour des fonctionnalités du langage C++ et leur mappage Visual c++, où un mappage de ce type existe et souligne les constructions pour lequel aucun mappage n’existe.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Plan des modifications (C++-CLI)](../dotnet/outline-of-changes-cpp-cli.md)  
 Un plan de haut niveau de référence rapide, en fournissant une liste des modifications sous cinq catégories générales.  
  
 [Mots clés de langage (C++-CLI)](../dotnet/language-keywords-cpp-cli.md)  
 Traite des modifications dans les mots clés du langage, y compris la suppression du trait de soulignement double et l’introduction de mots clés contextuels et espacés.  
  
 [Types managés (C + c++ / CL)](../dotnet/managed-types-cpp-cl.md)  
 Examine les modifications syntaxiques dans la déclaration du système de Type commun (CTS) - les modifications de la déclaration de classes, tableaux (y compris le tableau de paramètres), les énumérations et ainsi de suite.  
  
 [Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 Présente les modifications qui impliquent des membres de classe telles que les propriétés scalaires, les propriétés de l’index, les opérateurs, les délégués et les événements.  
  
 [Types valeur et leurs comportements (C++-CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 Se concentre sur les types valeur et la nouvelle famille de pointeurs intérieurs et épingles. Elle explique également plusieurs modifications sémantiques significatives telles que l’introduction de la conversion boxing implicite, que l’immuabilité de types valeur boxed et la suppression de la prise en charge pour les constructeurs par défaut dans les classes de valeur.  
  
 [Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)  
 Détaille des modifications sémantiques telles que la prise en charge pour la notation de cast, chaîne littérale comportement, ainsi que des modifications sémantiques entre ISO-C++ et c++ / CLI.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)