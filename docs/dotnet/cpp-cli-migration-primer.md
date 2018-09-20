---
title: C++ / c++ / CLI Migration Primer | Microsoft Docs
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
ms.openlocfilehash: 88b32ea226971c0fa5b6d269a8992629c3c4de77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385429"
---
# <a name="ccli-migration-primer"></a>Initiation à la migration de C++/CLI

Il s’agit d’un guide pour porter vos programmes Visual C++ d’Extensions managées pour C++ vers Visual C++.

C++ / c++ / CLI étend un paradigme de programmation de composants dynamiques au langage standard ISO-C++. Le nouveau langage offre plusieurs améliorations significatives sur les Extensions managées. Cette section fournit une énumération des Extensions managées pour les fonctionnalités du langage C++ et leur mappage à Visual C++, où un tel mappage existe, il signale également ces constructions pour lesquelles aucun mappage n’existe.

## <a name="in-this-section"></a>Dans cette section

[Plan des modifications (C++-CLI)](../dotnet/outline-of-changes-cpp-cli.md)<br/>
Un survol pour référence rapide, qui fournit une liste des modifications classées en cinq catégories générales.

[Mots clés de langage (C++-CLI)](../dotnet/language-keywords-cpp-cli.md)<br/>
Traite des modifications dans les mots clés du langage, y compris la suppression du trait de soulignement double et l’introduction de mots clés contextuels et espacés.

[Types managés (C++ / c++ / CL)](../dotnet/managed-types-cpp-cl.md)<br/>
Examine les modifications syntaxiques apportées à la déclaration du système de Type commun (CTS) - les modifications de la déclaration de classes, tableaux (y compris le tableau de paramètres), enums et ainsi de suite.

[Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
Présente les modifications qui concernent des membres de classe tels que les propriétés scalaires, les propriétés de l’index, les opérateurs, les délégués et les événements.

[Types valeur et leurs comportements (C++-CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
Se concentre sur les types valeur et la nouvelle famille de pointeurs intérieurs et épingles. Il aborde également plusieurs modifications sémantiques significatives telles que l’introduction de la conversion boxing implicite, l’immuabilité de types valeur boxed et la suppression de la prise en charge pour les constructeurs par défaut dans les classes value.

[Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
Détaille des modifications sémantiques telles que la prise en charge de la notation de cast, chaîne de comportement des littéraux et les modifications sémantiques entre ISO-C++ et C / c++ / CLI.

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)