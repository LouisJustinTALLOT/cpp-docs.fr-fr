---
description: En savoir plus sur:/VD (désactiver les déplacements de construction)
title: /vd (Désactiver les déplacements de construction)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: 9c90e2fa4f93ea0ba3892a07e13f2a15e848d608
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253193"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Désactiver les déplacements de construction)

## <a name="syntax"></a>Syntaxe

```
/vdn
```

## <a name="arguments"></a>Arguments

**0**<br/>
Supprime le membre de déplacement du constructeur/destructeur vtordisp. Choisissez cette option uniquement si vous êtes certain que tous les constructeurs et destructeurs de classe appellent des fonctions virtuelles virtuellement.

**1**<br/>
Active la création de membres de déplacement de constructeur/destructeur vtordisp masqués. Il s’agit du choix par défaut.

**2**<br/>
Vous permet d’utiliser [Dynamic_cast opérateur](../../cpp/dynamic-cast-operator.md) sur un objet en cours de construction. Par exemple, un dynamic_cast à partir d’une classe de base virtuelle vers une classe dérivée.

**/VD2** ajoute un champ vtordisp quand vous avez une base virtuelle avec des fonctions virtuelles. **/VD1** doit être suffisant. Le cas le plus courant où **/VD2** est nécessaire est lorsque la seule fonction virtuelle dans votre base virtuelle est un destructeur.

## <a name="remarks"></a>Notes

Ces options s’appliquent uniquement au code C++ qui utilise des bases virtuelles.

Visual C++ implémente la prise en charge du déplacement de la construction C++ dans les situations où l’héritage virtuel est utilisé. Les déplacements de construction résolvent le problème créé lorsqu’une fonction virtuelle, déclarée dans une base virtuelle et substituée dans une classe dérivée, est appelée à partir d’un constructeur pendant la construction d’une classe dérivée ultérieure.

Le problème est que la fonction virtuelle peut recevoir un pointeur incorrect **`this`** en raison d’incohérences entre les déplacements vers les bases virtuelles d’une classe et les déplacements vers ses classes dérivées. La solution fournit un seul ajustement de déplacement de construction, appelé champ vtordisp, pour chaque base virtuelle d’une classe.

Par défaut, les champs vtordisp sont introduits à chaque fois que le code définit des constructeurs et des destructeurs définis par l’utilisateur, et substitue également des fonctions virtuelles de bases virtuelles.

Ces options affectent l’ensemble des fichiers sources. Utilisez [vtordisp](../../preprocessor/vtordisp.md) pour supprimer puis réactiver les champs vtordisp classe par classe.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
