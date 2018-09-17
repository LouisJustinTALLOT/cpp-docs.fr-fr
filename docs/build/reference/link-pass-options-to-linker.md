---
title: -link (passer des Options à l’éditeur de liens) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 663407e4948ebc4e3c0a1676c44e8d2b4bd53fcc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704117"
---
# <a name="link-pass-options-to-linker"></a>/link (Passer des options à l'Éditeur de liens)

Passe une ou plusieurs options de l’éditeur de liens à l’éditeur de liens.

## <a name="syntax"></a>Syntaxe

```
/link linkeroptions
```

## <a name="arguments"></a>Arguments

*linkeroptions*<br/>
L’éditeur de liens les options à passer à l’éditeur de liens.

## <a name="remarks"></a>Notes

Le **/link** option et ses options de l’éditeur de liens doivent apparaître après les noms de fichiers et les options CL. Un espace est requis entre **/link,** et `linkeroptions`. Pour plus d’informations, consultez [définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur une page de propriétés de l’éditeur de liens.

1. Modifier une ou plusieurs propriétés.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option du compilateur ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)