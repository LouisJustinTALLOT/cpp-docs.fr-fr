---
title: /VERBOSE (Imprimer les messages d'avancement)
ms.date: 11/04/2016
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
ms.openlocfilehash: 7aed1e17034b40ffdad4da4136fc5a64361b3d77
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809143"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Imprimer les messages d'avancement)

```
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]
```

## <a name="remarks"></a>Notes

L’éditeur de liens envoie des informations sur la progression de la session de liaison à la **sortie** fenêtre. Sur la ligne de commande, les informations sont envoyées à la sortie standard et peuvent être redirigées vers un fichier.

|Option|Description|
|------------|-----------------|
|/VERBOSE|Affiche des détails sur le processus de liaison.|
|/ VERBOSE : LE PARE-FEU WINDOWS|Afficher des informations sur l’activité de l’éditeur de liens qui résulte de l’utilisation de [/OPT : ICF](opt-optimizations.md).|
|/ VERBOSE : INCR|Affiche des informations sur le processus d’édition de liens incrémentielle.|
|/ VERBOSE : LIB|Affiche des messages de progression indiquant uniquement les bibliothèques recherchées.<br /><br /> Les informations affichées incluant le processus de recherche de bibliothèque et répertorie chaque bibliothèque et nom d’objet (avec le chemin d’accès complet), le symbole est résolue à partir de la bibliothèque et une liste d’objets qui référencent le symbole.|
|/ VERBOSE : REF|Affiche des informations sur l’activité de l’éditeur de liens qui résulte de l’utilisation de [/OPT : REF](opt-optimizations.md).|
|/ VERBOSE : SAFESEH|Affiche des informations sur les modules qui ne sont pas compatibles avec sécurisée des exceptions lorsque [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) n’est pas spécifié.|
|/ VERBOSE : UNUSEDLIBS|Affiche des informations sur tous les fichiers de bibliothèque qui ne sont pas utilisés lors de la création de l’image.|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le **l’éditeur de liens** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Ajoutez l’option à la **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
