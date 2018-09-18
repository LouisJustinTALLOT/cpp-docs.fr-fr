---
title: -CLRTHREADATTRIBUTE (définir l’attribut de Thread CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea5b75c9f0691ef74c35ed405d64fc3389c4fcd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705794"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Définir l'attribut de thread CLR)

Spécifier explicitement l’attribut de thread pour le point d’entrée de votre programme CLR.

## <a name="syntax"></a>Syntaxe

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>Paramètres

**MTA**<br/>
S’applique l’attribut MTAThreadAttribute au point d’entrée de votre programme.

**NONE**<br/>
Identique à ne pas spécifier /CLRTHREADATTRIBUTE.  Permet de définir la valeur par défaut, attribut de thread Common Language Runtime (CLR).

**STA**<br/>
S’applique à l’attribut STAThreadAttribute au point d’entrée de votre programme.

## <a name="remarks"></a>Notes

Définition de l’attribut de thread est valide uniquement lors de la création d’un .exe, car il affecte le point d’entrée du thread principal.

Si vous utilisez le point d’entrée par défaut (main ou wmain, par exemple) spécifiez le modèle de thread en utilisant /CLRTHREADATTRIBUTE ou en plaçant l’attribut de thread (STAThreadAttribute ou MTAThreadAttribute) sur la fonction d’entrée par défaut.

Si vous utilisez un point d’entrée de celle par défaut, spécifiez le modèle de thread en utilisant /CLRTHREADATTRIBUTE ou en plaçant le threading attribut sur la fonction d’entrée non-par défaut, puis spécifiez le point d’entrée de celle par défaut avec [/Entry](../../build/reference/entry-entry-point-symbol.md) .

Si le modèle de thread spécifié dans le code source ne correspond pas avec le modèle de thread spécifié avec /CLRTHREADATTRIBUTE., l’éditeur de liens ignore /CLRTHREADATTRIBUTE et appliquer le modèle de thread spécifié dans le code source.

Il sera nécessaire pour pouvoir utiliser le thread unique, par exemple, si votre programme CLR héberge un objet COM qui utilise le thread unique.  Si votre programme CLR utilise le multithreading, il ne peut pas héberger un objet COM qui utilise le thread unique.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **avancé** page de propriétés.

1. Modifier le **l’attribut de Thread CLR** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)