---
description: En savoir plus sur:/await (activer la prise en charge de la Coroutine)
title: /await (Activer la prise en charge de la coroutine)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: a36c2233085a1c38ed61aed7d6ea757762179cc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182760"
---
# <a name="await-enable-coroutine-support"></a>/await (Activer la prise en charge de la coroutine)

Utilisez l’option du compilateur **/await** pour activer la prise en charge du compilateur pour les coroutines.

## <a name="syntax"></a>Syntaxe

> /await

## <a name="remarks"></a>Notes

L’option du compilateur **/await** active la prise en charge du compilateur pour les coroutines C++ et les mots clés **`co_await`** , **`co_yield`** et **`co_return`** . Cette option est désactivée par défaut. Pour plus d’informations sur la prise en charge des coroutines dans Visual Studio, consultez le blog de l' [équipe Visual Studio](https://devblogs.microsoft.com/cppblog/category/coroutine/). Pour plus d’informations sur la proposition standard de coroutines, consultez [ébauche de travail de N4628, spécification technique pour les extensions C++ pour les coroutines](https://wg21.link/n4628).

L’option **/await** est disponible à partir de Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet.

1. Sous **Propriétés de configuration**, développez le dossier **C/C++** , puis choisissez la page de propriétés **ligne de commande** .

1. Entrez l’option du compilateur **/await** dans la zone **options supplémentaires** . Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
