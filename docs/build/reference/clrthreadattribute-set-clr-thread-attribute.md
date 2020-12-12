---
description: En savoir plus sur:/CLRTHREADATTRIBUTE (définir l’attribut de thread CLR)
title: /CLRTHREADATTRIBUTE (Définir l'attribut de thread CLR)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
ms.openlocfilehash: 119797ee10ed0c08477b8e08635605e4299ffd41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179120"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Définir l'attribut de thread CLR)

Spécifiez explicitement l’attribut de thread pour le point d’entrée de votre programme CLR.

## <a name="syntax"></a>Syntaxe

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>Paramètres

**MTA**<br/>
Applique l’attribut MTAThreadAttribute au point d’entrée de votre programme.

**NONE**<br/>
Identique à ne pas spécifier/CLRTHREADATTRIBUTE.  Permet au Common Language Runtime (CLR) de définir l’attribut de thread par défaut.

**Single**<br/>
Applique l’attribut STAThreadAttribute au point d’entrée de votre programme.

## <a name="remarks"></a>Notes

La définition de l’attribut de thread est valide uniquement lors de la génération d’un fichier. exe, car il affecte le point d’entrée du thread principal.

Si vous utilisez le point d’entrée par défaut (main ou wmain, par exemple), spécifiez le modèle de thread à l’aide de/CLRTHREADATTRIBUTE ou en plaçant l’attribut de thread (STAThreadAttribute ou MTAThreadAttribute) sur la fonction d’entrée par défaut.

Si vous utilisez un point d’entrée autre que celui par défaut, spécifiez le modèle de thread à l’aide de/CLRTHREADATTRIBUTE ou en plaçant l’attribut de thread sur la fonction d’entrée non définie par défaut, puis spécifiez le point d’entrée non défini par défaut avec [/entry](entry-entry-point-symbol.md).

Si le modèle de thread spécifié dans le code source ne correspond pas au modèle de thread spécifié avec/CLRTHREADATTRIBUTE, l’éditeur de liens ignore/CLRTHREADATTRIBUTE et applique le modèle de thread spécifié dans le code source.

Il vous sera nécessaire d’utiliser le thread unique, par exemple, si votre programme CLR héberge un objet COM qui utilise un thread unique.  Si votre programme CLR utilise le multithreading, il ne peut pas héberger un objet COM qui utilise un thread unique.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez la page de propriétés **Avancé**.

1. Modifiez la propriété d' **attribut de thread CLR** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
