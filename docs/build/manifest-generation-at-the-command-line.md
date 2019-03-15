---
title: Génération de manifeste au niveau de la ligne de commande
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 37036ceedc59e20374fd1106a051ab2a66edd143
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820271"
---
# <a name="manifest-generation-at-the-command-line"></a>Génération de manifeste au niveau de la ligne de commande

Lorsque vous générez des applications C/C++ à partir de la ligne de commande à l’aide de nmake ou des outils similaires, le manifeste est généré une fois que l’éditeur de liens a traité tous les fichiers objets et construit le fichier binaire final. L’éditeur de liens recueille des informations d’assembly stockées dans les fichiers objets et combine ces informations dans un fichier de manifeste final. Par défaut, l’éditeur de liens génère un fichier nommé *nom_fichier_binaire*. *extension*.manifest pour décrire le fichier binaire final. L’éditeur de liens n’incorpore pas un fichier manifeste dans le fichier binaire et ne peut générer un manifeste comme un fichier externe. Il existe plusieurs façons d’incorporer un manifeste dans le fichier binaire final, par exemple à l’aide de la [outil manifeste (mt.exe)](https://msdn.microsoft.com/library/aa375649) ou en compilant le manifeste en un fichier de ressources. Il est important de n’oubliez pas que des règles spécifiques doivent être suivies lors de l’incorporation d’un manifeste dans le fichier binaire final pour activer des fonctionnalités telles que la liaison incrémentielle, signature, et Modifier & Continuer. Ces d’autres options sont traitées dans [Comment : Incorporer un manifeste à l’intérieur d’une Application C/C++](how-to-embed-a-manifest-inside-a-c-cpp-application.md) lors de la création de la ligne de commande.

## <a name="see-also"></a>Voir aussi

[Manifestes](/windows/desktop/sbscs/manifests)<br/>
[/INCREMENTAL (Lier par incrément)](reference/incremental-link-incrementally.md)<br/>
[Assemblys de nom fort (signature d’assembly) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Modifier & Continuer](/visualstudio/debugger/edit-and-continue)<br/>
[Présentation de la génération de manifeste pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
