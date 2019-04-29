---
title: '/ Zc : sizeddealloc (activer les fonctions de Global désallocation dimensionnée)'
ms.date: 03/06/2018
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
ms.openlocfilehash: dc381058c6a2ef84542be1d3cdd00c410aa51c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315480"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/ Zc : sizeddealloc (activer les fonctions de Global désallocation dimensionnée)

Le **/Zc : sizeddealloc** option du compilateur indique au compilateur d’appeler préférentiellement global `operator delete` ou `operator delete[]` fonctions qui ont un deuxième paramètre de type `size_t` lorsque la taille de l’objet est disponible. Ces fonctions peuvent utiliser le `size_t` paramètre pour optimiser les performances d’annulateur d’allocation.

## <a name="syntax"></a>Syntaxe

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>Notes

Dans la norme C ++ 11, vous pouvez définir des fonctions membres statiques `operator delete` et `operator delete[]` qui prendra une seconde, `size_t` paramètre. Généralement utilisées en association avec [opérateur new](../../cpp/new-operator-cpp.md) fonctions pour implémenter plus efficace des allocateurs et annulateurs d’allocation pour l’objet. Toutefois, C ++ 11 n’ont pas défini un ensemble équivalent des fonctions de désallocation dans une portée globale. Dans C ++ 11, désallocation global fonctions qui ont un deuxième paramètre de type `size_t` sont considérés comme des fonctions de suppression de sélection élective. Elles doivent être explicitement appelées en passant un argument de taille.

La norme C ++ 14 modifie le comportement du compilateur. Lorsque vous définissez global `operator delete` et `operator delete[]` qui accepte un deuxième paramètre de type `size_t`, le compilateur préfère d’appeler ces fonctions lorsque les versions de portée de membres ne sont pas appelées et la taille de l’objet est disponible. Le compilateur passe l’argument de taille implicitement. Les versions de l’argument unique sont appelées lorsque le compilateur ne peut pas déterminer la taille de l’objet désalloué. Sinon, les règles habituelles de choix de la version de la fonction de désallocation pour appeler s’appliquent toujours. Appels aux fonctions globales peuvent être spécifiées explicitement en ajoutant au début de l’opérateur de résolution de portée (`::`) à l’appel de fonction de désallocation.

Par défaut, Visual C++ à partir de Visual Studio 2015 implémente ce comportement par défaut 14 C ++. Vous pouvez explicitement spécifier cela en définissant le **/Zc : sizeddealloc** option du compilateur. Cela représente un risquer d’endommager le changement. Utiliser le **/Zc:sizedDealloc-** option pour conserver l’ancien comportement, par exemple, lorsque votre code définit des opérateurs de delete de positionnement qui utilisent un deuxième paramètre de type `size_t`. Les implémentations de bibliothèque de Visual Studio par défaut des fonctions de désallocation global ayant le deuxième paramètre de type `size_t` appeler les versions de paramètre unique. Si votre code fournit uniquement unique paramètre global de l’opérateur delete et d’opérateur delete [], les implémentations de bibliothèque par défaut des fonctions de désallocation dimensionnée global appeler vos fonctions globales.

Le **/Zc : sizeddealloc** option du compilateur est activée par défaut. Le [/ permissive-](permissive-standards-conformance.md) option n’affecte pas **/Zc : sizeddealloc**.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. À partir de la **Configurations** menu déroulant, choisissez **toutes les Configurations**.

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc : sizeddealloc** ou **/Zc:sizedDealloc-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
