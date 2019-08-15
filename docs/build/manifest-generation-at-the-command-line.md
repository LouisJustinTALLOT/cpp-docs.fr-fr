---
title: Génération de manifeste au niveau de la ligne de commande
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493201"
---
# <a name="manifest-generation-at-the-command-line"></a>Génération de manifeste au niveau de la ligne de commande

Lors de la générationC++ de C/applications à partir de la ligne de commande à l’aide de NMAKE ou d’outils similaires, le manifeste est généré après que l’éditeur de liens a traité tous les fichiers objets et créé le fichier binaire final. L’éditeur de liens collecte les informations d’assembly stockées dans les fichiers objets et combine ces informations dans un fichier manifeste final. Par défaut, l’éditeur de liens génère un fichier nommé *binary_name*. *extension*. manifest pour décrire le fichier binaire final. L’éditeur de liens n’incorpore pas de fichier manifeste dans le fichier binaire et ne peut générer qu’un manifeste en tant que fichier externe. Il existe plusieurs façons d’incorporer un manifeste à l’intérieur du fichier binaire final, par exemple en utilisant l' [outil manifeste (Mt. exe)](/windows/win32/sbscs/mt-exe) ou en compilant le manifeste dans un fichier de ressources. Il est important de garder à l’esprit que des règles spécifiques doivent être suivies lors de l’incorporation d’un manifeste à l’intérieur du fichier binaire final pour activer des fonctionnalités telles que la liaison incrémentielle, la signature et la modification et la poursuite de l’opération. Ces options et d’autres sont décrites [dans How to: Incorporez un manifeste à l’intérieurC++ d'](how-to-embed-a-manifest-inside-a-c-cpp-application.md) une application C/lors de la génération sur la ligne de commande.

## <a name="see-also"></a>Voir aussi

[Manifestes](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (Lier par incrément)](reference/incremental-link-incrementally.md)<br/>
[Assemblys de nom fort (signature d’assembly) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Modifier & Continuer](/visualstudio/debugger/edit-and-continue)<br/>
[Présentation de la génération de manifeste pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
