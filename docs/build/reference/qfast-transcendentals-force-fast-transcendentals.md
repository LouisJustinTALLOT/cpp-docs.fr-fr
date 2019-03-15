---
title: /Qfast_transcendentals (Force Fast Transcendentals)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 383a915721d627367ca2ca035957df947996bbe2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818347"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Force Fast Transcendentals)

Génère du code inline pour les fonctions transcendantes.

## <a name="syntax"></a>Syntaxe

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Notes

Cette option du compilateur force des fonctions transcendantes à convertir en code inline pour améliorer la vitesse d’exécution. Cette option a un effet uniquement en association avec **/fp : sauf** ou **/fp : precise**. Génération du code incorporé pour les fonctions transcendantes est déjà le comportement par défaut sous **Fast**.

Cette option n’est pas compatible avec **/fp : strict**. Consultez [/fp (spécifier le comportement de virgule flottante)](fp-specify-floating-point-behavior.md) pour plus d’informations sur flottante options du compilateur de point.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
