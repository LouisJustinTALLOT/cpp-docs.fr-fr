---
description: 'En savoir plus sur:/Zc : sizedDealloc (activer les fonctions de désallocation dimensionnées globales)'
title: '/Zc : sizedDealloc (activer les fonctions de désallocation dimensionnées globales)'
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
ms.openlocfilehash: 4e40355dc3c61f725ca9996dc4c91c0604866fe4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269066"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc : sizedDealloc (activer les fonctions de désallocation dimensionnées globales)

L’option de compilateur **/Zc : sizedDealloc** indique au compilateur d’appeler de manière préférentielle globale `operator delete` ou des `operator delete[]` fonctions qui ont un deuxième paramètre de type `size_t` lorsque la taille de l’objet est disponible. Ces fonctions peuvent utiliser le `size_t` paramètre pour optimiser les performances de annulateur.

## <a name="syntax"></a>Syntaxe

> **/Zc : sizedDealloc**[ **-** ]

## <a name="remarks"></a>Notes

Dans la norme C++ 11, vous pouvez définir des fonctions membres statiques `operator delete` et `operator delete[]` qui prennent un deuxième `size_t` paramètre,. En général, ceux-ci sont utilisés en association avec les [nouvelles fonctions Operator](../../cpp/new-operator-cpp.md) pour implémenter des allocateurs et des annulateurs plus efficaces pour l’objet. Toutefois, C++ 11 n’a pas défini un jeu équivalent de fonctions de désallocation au niveau de la portée globale. En C++ 11, les fonctions de désallocation globale qui ont un deuxième paramètre de type `size_t` sont considérées comme des fonctions de suppression de placement. Ils doivent être appelés explicitement en passant un argument de taille.

La norme C++ 14 modifie le comportement du compilateur. Lorsque vous définissez global `operator delete` et `operator delete[]` que vous prenez un deuxième paramètre de type `size_t` , le compilateur préfère appeler ces fonctions lorsque les versions de portée de membre ne sont pas appelées et que la taille de l’objet est disponible. Le compilateur passe l’argument de taille implicitement. Les versions d’arguments uniques sont appelées lorsque le compilateur ne peut pas déterminer la taille de l’objet qui est libéré. Dans le cas contraire, les règles habituelles pour le choix de la version de la fonction de désallocation à appeler s’appliquent toujours. Les appels aux fonctions globales peuvent être spécifiés explicitement en ajoutant l’opérateur de résolution `::` de portée () à l’appel de fonction de désallocation.

Par défaut, Visual C++ à partir de Visual Studio 2015 implémente ce comportement standard C++ 14. Vous pouvez spécifier explicitement cela en définissant l’option de compilateur **/Zc : sizedDealloc** . Cela représente une modification potentiellement rupture. Utilisez l’option **/Zc : sizedDealloc-** pour conserver l’ancien comportement, par exemple, lorsque votre code définit des opérateurs de suppression de placement qui utilisent un deuxième paramètre de type `size_t` . Les implémentations de la bibliothèque Visual Studio par défaut des fonctions de désallocation globale qui ont le deuxième paramètre de type `size_t` appellent les versions de paramètre uniques. Si votre code fournit uniquement un opérateur global à un seul paramètre et un opérateur delete [], les implémentations de la bibliothèque par défaut des fonctions de désallocation dimensionnées globales appellent vos fonctions globales.

L’option de compilateur **/Zc : sizedDealloc** est activée par défaut. L’option [/permissive-](permissive-standards-conformance.md) n’a pas d’incidence sur **/Zc : sizedDealloc**.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le menu déroulant **configurations** , choisissez **toutes les configurations**.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : sizedDealloc** ou **/Zc : SizedDealloc-** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
