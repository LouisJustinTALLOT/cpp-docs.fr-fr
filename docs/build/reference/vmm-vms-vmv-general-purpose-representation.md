---
title: / VMM, - vms, - vmv (représentation à but général)
ms.date: 11/04/2016
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
ms.openlocfilehash: 7a46cecdbf96ad891ce218df4769a60590e562a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316728"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (Représentation à but général)

Utilisé lorsque [/vmb, /vmg (méthode de représentation)](vmb-vmg-representation-method.md) est sélectionné comme le [méthode de représentation](vmb-vmg-representation-method.md). Ces options indiquent le modèle d’héritage de la définition de classe a pas encore été rencontrée.

## <a name="syntax"></a>Syntaxe

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>Notes

Les options sont décrites dans le tableau suivant.

|Option|Description|
|------------|-----------------|
|**/vmm**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe pour qu’il utilise l’héritage multiple.<br /><br /> Correspondants [mot clé d’héritage](../../cpp/inheritance-keywords.md) et l’argument de [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **héritages multiples**.<br /><br /> Cette représentation est supérieure à celle requise pour l’héritage unique.<br /><br /> Si le modèle d’héritage d’une définition de classe pour laquelle un pointeur vers un membre est déclaré est virtuel, le compilateur génère une erreur.|
|**/vms**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe pour qu’il n’utilise pas l’héritage ou un héritage simple.<br /><br /> Correspondants [mot clé d’héritage](../../cpp/inheritance-keywords.md) et l’argument de [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **héritage unique**.<br /><br /> Il s’agit de la plus petite représentation possible d’un pointeur vers un membre d’une classe.<br /><br /> Si le modèle d’héritage d’une définition de classe pour laquelle un pointeur vers un membre est déclaré est de type multiple ou virtuel, le compilateur génère une erreur.|
|**/vmv**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe pour qu’il utilise l’héritage virtuel. Il jamais provoque une erreur et la valeur par défaut.<br /><br /> Correspondants [mot clé d’héritage](../../cpp/inheritance-keywords.md) et l’argument de [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **virtual_inheritance**.<br /><br /> Cette option nécessite un pointeur plus large et du code supplémentaire pour interpréter le pointeur que les autres options.|

Lorsque vous spécifiez une de ces options de modèle d’héritage, ce modèle est utilisé pour tous les pointeurs vers des membres de classe, quel que soit leur type d’héritage ou si le pointeur est déclaré avant ou après la classe. Par conséquent, si vous utilisez toujours des classes d’héritage simple, vous pouvez réduire la taille du code en compilant avec **/VMS**; Toutefois, si vous souhaitez utiliser la plupart des cas (aux dépens de la représentation de données), compilez avec **/vmv**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/vmb, /vmg (Méthode de représentation)](vmb-vmg-representation-method.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
