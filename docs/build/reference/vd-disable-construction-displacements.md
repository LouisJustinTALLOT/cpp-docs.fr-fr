---
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
ms.openlocfilehash: a3e09bf923f9f77dfb594c598f8a14c766d052f8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426415"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Désactiver les déplacements de construction)

## <a name="syntax"></a>Syntaxe

```
/vdn
```

## <a name="arguments"></a>Arguments

**0**<br/>
Supprime le membre de déplacement de constructeur/destructeur vtordisp. Choisissez cette option uniquement si vous êtes certain que tous les constructeurs de classe et les destructeurs appellent virtuels virtuellement les fonctions.

**1**<br/>
Permet la création de membres de déplacement de constructeur/destructeur vtordisp masqué. Ce choix est la valeur par défaut.

**2**<br/>
Vous permet d’utiliser [opérateur dynamic_cast](../../cpp/dynamic-cast-operator.md) sur un objet en cours de construction. Par exemple, il s’agit d’un dynamic_cast de la classe de base virtuelle vers une classe dérivée.

**/ vd2** ajoute un champ vtordisp lorsque vous disposez d’une base virtuelle avec des fonctions virtuelles. **/ vd1** devraient suffire. La plus courante de cas où **/vd2** est nécessaire est lorsque la seule fonction virtuelle dans votre base virtuelle est un destructeur.

## <a name="remarks"></a>Notes

Ces options s’appliquent uniquement au code C++ qui utilise des bases virtuelles.

Visual C++ implémente la prise en charge de déplacement de construction C++ dans les cas où l’héritage virtuel est utilisé. Les déplacements de construction résoudre le problème créé lors d’une fonction virtuelle, déclarée dans une base virtuelle et de substitution dans une classe dérivée, est appelée à partir d’un constructeur pendant la construction d’une classe dérivée supplémentaire.

Le problème est que la fonction virtuelle peut recevoir un incorrect `this` pointeur ainsi de différences existant entre les déplacements vers le virtuel bases d’une classe et les déplacements à ses classes dérivées. La solution fournit un ajustement de déplacement de construction unique, appelé champ vtordisp, pour chaque base virtuelle d’une classe.

Par défaut, les champs vtordisp sont introduits chaque fois que le code définit des destructeurs et des constructeurs définis par l’utilisateur et remplace également des fonctions virtuelles des bases virtuelles.

Ces options affectent l’ensemble des fichiers sources. Utilisez [vtordisp](../../preprocessor/vtordisp.md) à supprimer, puis réactiver les champs vtordisp classe par classe.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
