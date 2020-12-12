---
description: En savoir plus sur:/VMM,/VMS,/vmv (représentation usage général)
title: /VMM,-machines virtuelles,-vmv (représentation usage général)
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
ms.openlocfilehash: 8c5761a2f51ec9860a4afeb7d4aacbf7f882b3f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257223"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (Représentation à but général)

Utilisé lorsque [/VMB,/vmg (méthode de représentation)](vmb-vmg-representation-method.md) est sélectionné comme [méthode de représentation](vmb-vmg-representation-method.md). Ces options indiquent le modèle d’héritage de la définition de classe qui n’est pas encore rencontrée.

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
|**/VMM**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe qui utilise l’héritage multiple.<br /><br /> Le [mot clé](../../cpp/inheritance-keywords.md) et l’argument d’héritage correspondants pour [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **multiple_inheritance**.<br /><br /> Cette représentation est supérieure à celle requise pour l’héritage unique.<br /><br /> Si le modèle d’héritage d’une définition de classe pour laquelle un pointeur vers un membre est déclaré est virtuel, le compilateur génère une erreur.|
|**/VMS**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe qui n’utilise aucun héritage ou héritage unique.<br /><br /> Le [mot clé](../../cpp/inheritance-keywords.md) et l’argument d’héritage correspondants pour [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **single_inheritance**.<br /><br /> Il s’agit de la plus petite représentation possible d’un pointeur vers un membre d’une classe.<br /><br /> Si le modèle d’héritage d’une définition de classe pour laquelle un pointeur vers un membre est déclaré est multiple ou virtuel, le compilateur génère une erreur.|
|**/vmv**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe qui utilise l’héritage virtuel. Elle ne génère jamais d’erreur et est la valeur par défaut.<br /><br /> Le [mot clé](../../cpp/inheritance-keywords.md) et l’argument d’héritage correspondants pour [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **virtual_inheritance**.<br /><br /> Cette option requiert un pointeur plus grand et du code supplémentaire pour interpréter le pointeur par rapport aux autres options.|

Lorsque vous spécifiez l’une de ces options de modèle d’héritage, ce modèle est utilisé pour tous les pointeurs vers des membres de classe, quel que soit leur type d’héritage ou si le pointeur est déclaré avant ou après la classe. Par conséquent, si vous utilisez toujours des classes d’héritage unique, vous pouvez réduire la taille du code en compilant avec **/VMS**; Toutefois, si vous souhaitez utiliser le cas le plus général (au détriment de la plus grande représentation des données), compilez avec **/vmv**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/vmb,/vmg (méthode de représentation)](vmb-vmg-representation-method.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
