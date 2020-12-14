---
description: En savoir plus sur:/RELEASE (définir la somme de contrôle)
title: /RELEASE (Définir le total de Checksum)
ms.date: 11/04/2016
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
ms.openlocfilehash: ed1e55dffb02ace26e91e262bd3e9514f056196e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225321"
---
# <a name="release-set-the-checksum"></a>/RELEASE (Définir le total de Checksum)

```
/RELEASE
```

## <a name="remarks"></a>Notes

L’option/RELEASE définit la somme de contrôle dans l’en-tête d’un fichier. exe.

Le système d’exploitation requiert la somme de contrôle des pilotes de périphérique. Définissez la somme de contrôle des versions release de vos pilotes de périphérique pour garantir la compatibilité avec les futurs systèmes d’exploitation.

L’option/RELEASE est définie par défaut lorsque l’option [/SUBSYSTEM : Native](subsystem-specify-subsystem.md) est spécifiée.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **avancé** .

1. Modifiez la propriété **définir la somme de contrôle** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
