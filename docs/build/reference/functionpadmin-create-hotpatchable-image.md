---
description: En savoir plus sur:/FUNCTIONPADMIN (créer une image corrigeable en mémoire)
title: /FUNCTIONPADMIN (Création d'une image corrigeable en mémoire)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: f86adb2001adacf1b6c8a03a90b7452505841c08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192003"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Création d'une image corrigeable en mémoire)

Prépare une image pour la mise à jour à chaud.

## <a name="syntax"></a>Syntaxe

> **/FUNCTIONPADMIN**[**:**_Space_]

### <a name="arguments"></a>Arguments

*espace*<br/>
Quantité de remplissage à ajouter au début de chaque fonction en octets. Sur x86, la valeur par défaut est 5 octets de remplissage et, sur x64, la valeur par défaut est 6 octets. Sur les autres cibles, une valeur doit être fournie.

## <a name="remarks"></a>Notes

Pour que l’éditeur de liens produise une image corrigeable en mémoire, les fichiers. obj doivent avoir été compilés avec [/hotpatch (créer une image corrigeable en mémoire)](hotpatch-create-hotpatchable-image.md).

Quand vous compilez et liez une image avec un appel unique de cl.exe, **/hotpatch** implique **/FUNCTIONPADMIN**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Entrez l’option **/FUNCTIONPADMIN** dans **options supplémentaires**. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
