---
description: En savoir plus sur:/YD (placer les informations de débogage dans un fichier objet)
title: /Yd (Placer les informations de débogage dans un fichier objet)
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: 7716d5ca1893faefac9186f97e2f7439a3887343
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243586"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Placer les informations de débogage dans un fichier objet)

Répartir les informations de débogage complètes dans tous les fichiers objets créés à partir d’un fichier d’en-tête précompilé (. pch) lorsqu’ils sont utilisés avec les options [/Yc](yc-create-precompiled-header-file.md) et [/Z7](z7-zi-zi-debug-information-format.md) . Action déconseillée.

## <a name="syntax"></a>Syntaxe

```
/Yd
```

## <a name="remarks"></a>Notes

**/Yd** est déconseillé ; Visual C++ prend maintenant en charge l’écriture de plusieurs objets dans un seul fichier. pdb, utilisez **/Zi** à la place. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

À moins que vous n’ayez besoin de distribuer une bibliothèque contenant des informations de débogage, utilisez l’option [/Zi](z7-zi-zi-debug-information-format.md) plutôt que **/Z7** et **/Yd**.

Le stockage des informations de débogage complètes dans chaque fichier. obj est nécessaire uniquement pour distribuer des bibliothèques qui contiennent des informations de débogage. Elle ralentit la compilation et nécessite un espace disque considérable. Lorsque **/Yc** et **/Z7** sont utilisés sans **/Yd**, le compilateur stocke les informations de débogage courantes dans le premier fichier. obj créé à partir du fichier. pch. Le compilateur n’insère pas ces informations dans les fichiers. obj créés par la suite à partir du fichier. pch ; Elle insère des références croisées aux informations. Quel que soit le nombre de fichiers. obj qui utilisent le fichier. pch, un seul fichier. obj contient les informations de débogage courantes.

Bien que ce comportement par défaut entraîne des temps de génération plus rapides et une réduction des besoins en espace disque, il n’est pas souhaitable si une petite modification nécessite de reconstruire le fichier. obj contenant les informations de débogage courantes. Dans ce cas, le compilateur doit régénérer tous les fichiers. obj qui contiennent des références croisées au fichier. obj d’origine. En outre, si un fichier. pch commun est utilisé par des projets différents, il est difficile de se fier aux références croisées à un seul fichier. obj.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [/Y (en-têtes précompilés)](y-precompiled-headers.md)

- [Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Exemples

Supposons que vous disposiez de deux fichiers de base, F. cpp et G. cpp, chacun contenant les instructions **#include** suivantes :

```
#include "windows.h"
#include "etc.h"
```

La commande suivante crée le fichier d’en-tête précompilé, ETC. pch, ainsi que le fichier objet F. obj :

```
CL /YcETC.H /Z7 F.CPP
```

Le fichier objet F. obj inclut des informations sur le type et le symbole pour WINDOWS. h et ETC. h (et tous les autres fichiers d’en-tête inclus). Vous pouvez maintenant utiliser l’en-tête précompilé, ETC. pch pour compiler le fichier source G. cpp :

```
CL /YuETC.H /Z7 G.CPP
```

Le fichier objet G. obj n’inclut pas les informations de débogage pour l’en-tête précompilé, mais fait simplement référence à ces informations dans le fichier F. obj. Notez que vous devez créer un lien avec le fichier F. obj.

Si votre en-tête précompilé n’a pas été compilé avec **/Z7**, vous pouvez toujours l’utiliser dans des compilations ultérieures à l’aide de **/Z7**. Toutefois, les informations de débogage sont placées dans le fichier objet actuel, et les symboles locaux pour les fonctions et les types définis dans l’en-tête précompilé ne sont pas disponibles pour le débogueur.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
