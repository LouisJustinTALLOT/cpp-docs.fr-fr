---
description: En savoir plus sur:/VERBOSE (imprimer les messages d’avancement)
title: /VERBOSE (Afficher les messages de progression)
ms.date: 06/13/2019
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: 9d1a22a1b05f42a707b2449fbb114ba06db85ff5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176416"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Afficher les messages de progression)

Génère des messages de progression pendant le processus de liaison.

## <a name="syntax"></a>Syntaxe

> **/Verbose** \[ **:**{**CLR** | **ICF** | **incr** | **lib** | **ref** |  | **UNUSEDDELAYLOAD** | **UNUSEDLIBS**}\]

## <a name="remarks"></a>Notes

L’éditeur de liens envoie des informations sur la progression de la session de liaison à la fenêtre **sortie** . Sur la ligne de commande, les informations sont envoyées à la sortie standard et peuvent être redirigées vers un fichier.

| Option | Description |
| ------------ | ----------------- |
| /VERBOSE | Affiche des détails sur le processus de liaison. |
| /VERBOSE : CLR | Affiche des informations sur l’activité de l’éditeur de liens propre aux objets et aux métadonnées compilées à l’aide de [/CLR](clr-common-language-runtime-compilation.md). |
| /VERBOSE : ICF | Affiche des informations sur l’activité de l’éditeur de liens qui résulte de l’utilisation de [/OPT : ICF](opt-optimizations.md). |
| /VERBOSE : INCR | Affiche des informations sur le processus de liaison incrémentielle. |
| /VERBOSE : LIB | Affiche des messages de progression qui indiquent uniquement les bibliothèques recherchées.<br/> Les informations affichées incluent le processus de recherche dans la bibliothèque. Elle répertorie chaque bibliothèque et nom d’objet (avec le chemin d’accès complet), le symbole qui est résolu à partir de la bibliothèque et une liste d’objets qui référencent le symbole. |
| /VERBOSE : REF | Affiche des informations sur l’activité de l’éditeur de liens qui résulte de l’utilisation de [/OPT : Ref](opt-optimizations.md). |
| /VERBOSE : SAFESEH | Affiche des informations sur les modules qui sont incompatibles avec la gestion de la sécurité structurée des exceptions lorsque [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) n’est pas spécifié. |
| /VERBOSE : UNUSEDDELAYLOAD | Affiche des informations sur les dll à chargement différé qui n’ont aucun symbole utilisé lors de la création de l’image. |
| /VERBOSE : UNUSEDLIBS | Affiche des informations sur tous les fichiers de bibliothèque qui ne sont pas utilisés lors de la création de l’image. |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Ajoutez l’option à la zone **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
