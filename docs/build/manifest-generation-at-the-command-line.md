---
description: 'En savoir plus sur : génération de manifeste à partir de la ligne de commande'
title: Génération de manifeste au niveau de la ligne de commande
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 30b826e0fe98a143f58d7987203881a8fd8e601b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176455"
---
# <a name="manifest-generation-at-the-command-line"></a>Génération de manifeste au niveau de la ligne de commande

Lors de la génération d’applications C/C++ à partir de la ligne de commande à l’aide de NMAKE ou d’outils similaires, le manifeste est généré après que l’éditeur de liens a traité tous les fichiers objets et créé le fichier binaire final. L’éditeur de liens collecte les informations d’assembly stockées dans les fichiers objets et combine ces informations dans un fichier manifeste final. Par défaut, l’éditeur de liens génère un fichier nommé *binary_name*. *extension*. manifest pour décrire le fichier binaire final. L’éditeur de liens n’incorpore pas de fichier manifeste dans le fichier binaire et ne peut générer qu’un manifeste en tant que fichier externe. Il existe plusieurs façons d’incorporer un manifeste à l’intérieur du fichier binaire final, par exemple en utilisant l' [outil manifeste (mt.exe)](/windows/win32/sbscs/mt-exe) ou en compilant le manifeste dans un fichier de ressources. Il est important de garder à l’esprit que des règles spécifiques doivent être suivies lors de l’incorporation d’un manifeste à l’intérieur du fichier binaire final pour activer des fonctionnalités telles que la liaison incrémentielle, la signature et la modification et la poursuite de l’opération. Ces options et d’autres sont décrites dans [Comment : incorporer un manifeste à l’intérieur d’une application C/C++](how-to-embed-a-manifest-inside-a-c-cpp-application.md) lors de la génération sur la ligne de commande.

## <a name="see-also"></a>Voir aussi

[Manifestes](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (lier par incrément)](reference/incremental-link-incrementally.md)<br/>
[Assemblys de nom fort (signature d’assembly) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Modifier &amp; Continuer](/visualstudio/debugger/edit-and-continue)<br/>
[Fonctionnement de la génération de manifestes pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
