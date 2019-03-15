---
title: /link (Passer des options à l'Éditeur de liens)
ms.date: 11/04/2016
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: 7f40841b82db9f46019ce2a96a61a1a0f622b6d5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813433"
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

Le **/link** option et ses options de l’éditeur de liens doivent apparaître après les noms de fichiers et les options CL. Un espace est requis entre **/link,** et `linkeroptions`. Pour plus d’informations, consultez [référence de l’éditeur de liens MSVC](linking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur une page de propriétés de l’éditeur de liens.

1. Modifier une ou plusieurs propriétés.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option du compilateur ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
