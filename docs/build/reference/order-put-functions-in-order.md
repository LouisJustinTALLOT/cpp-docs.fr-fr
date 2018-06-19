---
title: -ORDRE (mettre les fonctions dans l’ordre) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
dev_langs:
- C++
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de9b0fb629a1bf984929ec170f05e25e740e9cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378481"
---
# <a name="order-put-functions-in-order"></a>/ORDER (Mettre les fonctions dans l'ordre)

Spécifier l’ordre de liaison pour les fonctions séparément empaquetées (COMDAT).

## <a name="syntax"></a>Syntaxe

>/ COMMANDE : @*nom de fichier*

### <a name="parameters"></a>Paramètres

*filename*  
Un fichier texte qui spécifie l’ordre de liaison des fonctions COMDAT.

## <a name="remarks"></a>Notes

Le **/Order** option du compilateur vous permet d’optimiser le comportement de pagination de votre programme en regroupant une fonction avec les fonctions qu’elle appelle. Vous pouvez également regrouper les fonctions appelées fréquemment ensemble. Ces techniques, appelés *réglage de l’échange* ou *l’optimisation de la pagination*, augmente la probabilité qu’une fonction appelée est en mémoire lorsqu’il est nécessaire et ne doit pas être notifié par radiomessagerie à partir du disque.

Lorsque vous compilez votre code source dans un fichier objet, vous pouvez indiquer au compilateur pour placer chaque fonction dans sa propre section appelée un *COMDAT*, à l’aide de la [/Gy (activer la liaison au niveau des fonctions)](../../build/reference/gy-enable-function-level-linking.md) compilateur option. Le **/Order** option de l’éditeur de liens indique à l’éditeur de liens place les COMDAT dans l’image exécutable dans l’ordre que vous spécifiez.

Pour spécifier l’ordre des COMDAT, créez un *fichier réponse*, un fichier texte qui répertorie chaque COMDAT par nom, un par ligne, dans l’ordre que vous sélectionnez soient placés par l’éditeur de liens. Passez le nom de ce fichier en tant que le *nom de fichier* paramètre de la **/Order** option. Pour les fonctions C++, le nom d’un COMDAT est la forme décorée du nom de la fonction. Utiliser le nom non décoré pour les fonctions C, `main`, ainsi que pour les fonctions C++ déclarées comme `extern "C"`. Les noms de fonctions et les noms décorés respectent la casse. Pour plus d’informations sur les noms décorés, consultez [noms décorés](../../build/reference/decorated-names.md). 

Pour rechercher les noms décorés de votre COMDAT, utilisez le [DUMPBIN](../../build/reference/dumpbin-reference.md) l’outil [/symboles](../../build/reference/symbols.md) option sur le fichier objet. L’éditeur de liens ajoute automatiquement un trait de soulignement (\_) à la fonction de noms dans la réponse de fichiers, sauf si le nom commence par un point d’interrogation ( ?) ou signe arobase (@). Par exemple, si un fichier source, example.cpp, contient des fonctions `int cpp_func(int)`, `extern "C" int c_func(int)` et `int main(void)`, la commande `DUMPBIN /SYMBOLS example.obj` répertorie ces noms décorés :

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

Dans ce cas, spécifiez les noms en tant que `?cpp_func@@YAHH@Z`, `c_func`, et `main` dans votre fichier de réponse.

Si plusieurs **/Order** option s’affiche dans les options de l’éditeur de liens, la dernière spécifiée est appliquée.

Le **/Order** option désactive les liens incrémentiels. Vous pouvez voir l’avertissement de l’éditeur de liens [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) lorsque vous spécifiez cette option si la liaison incrémentielle est activée, ou si vous avez spécifié le [/ZI (incrémentielle PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) option du compilateur. Pour exclure cet avertissement, vous pouvez utiliser la [/INCREMENTAL : no](../../build/reference/incremental-link-incrementally.md) option de l’éditeur de liens pour désactiver les liens incrémentiels et utiliser le [/ZI (générer PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) option du compilateur pour générer un fichier PDB sans édition des liens incrémentielle.

> [!NOTE]
> LIEN ne peut pas classer les fonctions statiques car les noms de fonctions statiques ne sont pas des noms de symboles publics. Lorsque **/Order** est spécifié, l’avertissement de l’éditeur de liens [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) est généré pour chaque symbole dans le fichier de réponse de commande est statique ou introuvable.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  

1. Sous **propriétés de Configuration**, ouvrez **l’éditeur de liens** , puis choisissez le **optimisation** page de propriétés.

1. Modifier la **fonction ordre** propriété pour contenir le nom de votre fichier de réponse.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)  
[Options de l’éditeur de liens](../../build/reference/linker-options.md)