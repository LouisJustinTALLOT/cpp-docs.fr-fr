---
title: Erreur des outils Éditeur de liens LNK2001
ms.date: 05/17/2017
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: 824fa9108e6322b1bcf77d6c28c7fb843b743833
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161015"
---
# <a name="linker-tools-error-lnk2001"></a>Erreur des outils Éditeur de liens LNK2001

symbole externe non résolu »*symbole*»

Le code compilé effectue une référence ou un appel à *symbole*, mais ce symbole n’est pas défini dans les bibliothèques ou des fichiers objets spécifiés à l’éditeur de liens.

Ce message d’erreur est suivi d’une erreur irrécupérable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Vous devez corriger les erreurs de tous les LNK2001 et l’erreur LNK2019 pour corriger l’erreur LNK1120.

## <a name="possible-causes"></a>Causes possibles

Il existe plusieurs façons d’obtenir cette erreur, mais tous les impliquent une référence à une fonction ou une variable qui n’est pas de l’éditeur de liens *résoudre*, ou de trouver une définition pour. Le compilateur peut identifier quand un symbole n’est pas *déclaré*, mais pas quand il n’est pas *défini*, car la définition peut être dans un autre fichier source ou la bibliothèque. Si un symbole est appelé, mais jamais défini, l’éditeur de liens génère une erreur.

### <a name="coding-issues"></a>Problèmes de codage

Cette erreur peut être provoquée par la casse ne correspondent pas dans votre code source ou la définition de module (.def) fichier. Par exemple, si vous nommez une variable `var1` dans un C++ fichier source et essayez d’y accéder en tant que `VAR1` dans une autre, cette erreur est générée. Pour résoudre ce problème, utilisez systématiquement orthographié et la casse des noms.

Cette erreur peut être provoquée dans un projet qui utilise [des fonctions inline](../../error-messages/tool-errors/function-inlining-problems.md) si vous définissez les fonctions dans un fichier source, plutôt que dans un fichier d’en-tête. Fonctions inline ne sont pas visibles en dehors du fichier source qui les définit. Pour résoudre ce problème, définissez les fonctions inline dans les en-têtes dans lesquels ils sont déclarés.

Cette erreur peut être provoquée si vous appelez une fonction C à partir d’un programme C++ sans utiliser un `extern "C"` déclaration de la fonction C. Le compilateur utilise les conventions d’affectation de noms autre symbole interne pour le code C et C++, et c’est le nom de symbole interne qui l’éditeur de liens recherche lors de la résolution des symboles. Pour résoudre ce problème, utilisez un `extern "C"` wrapper autour de toutes les déclarations de fonctions C utilisées dans votre code C++, ce qui entraîne le compilateur à utiliser la convention d’affectation de noms interne C pour ces symboles. Options du compilateur [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) et [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) contraindre le compilateur compiler les fichiers sous forme C++ ou C, respectivement, quelle que soit l’extension de nom de fichier. Ces options peuvent provoquer des noms de fonction interne différentes de ce que vous attendez.

Cette erreur peut être dû à une tentative pour référencer des fonctions ou des données qui n’ont pas une liaison externe. En C++, les fonctions inline et `const` données ont une liaison interne sauf spécification explicite en tant que `extern`. Pour résoudre ce problème, utilisez explicite `extern` déclarations sur symboles appelée en dehors du fichier de source de définition.

Cette erreur peut être provoquée par un [corps de fonction ou variable manquant](../../error-messages/tool-errors/missing-function-body-or-variable.md) définition. Cette erreur est courant lorsque vous déclarez, mais que vous ne définissez pas, variables, fonctions ou classes dans votre code. Le compilateur a uniquement besoin d’un prototype de fonction ou `extern` déclaration de variable pour générer un fichier d’objet sans erreur, mais l’éditeur de liens ne peut pas résoudre un appel à la fonction ou une référence à la variable, car il n’existe aucun espace de code ou une variable (fonction) réservé. Pour résoudre ce problème, assurez-vous que chaque fonction référencée et la variable sont entièrement défini dans un fichier source ou de la bibliothèque inclus dans votre lien.

Cette erreur peut être provoquée par un appel de fonction qui utilise les types de retour et de paramètres ou les conventions d’appel qui ne correspondent pas à celles figurant dans la définition de fonction. Dans les fichiers d’objet C++, [décoration de nom](../../error-messages/tool-errors/name-decoration.md) incorpore la convention d’appel, portée de classe ou espace de noms et les types de retour et de paramètres d’une fonction dans le nom décoré final de la fonction, qui est utilisé comme symbole à correspondent lorsque les appels à la fonction à partir d’autres fichiers objets sont résolus. Pour résoudre ce problème, assurez-vous que la déclaration, définition et les appels à la fonction toutes les utilisent les mêmes étendues, les types et les conventions d’appel.

Cette erreur peut être provoquée dans du code C++, lorsque vous incluez un prototype de fonction dans une définition de classe, mais ne parviennent pas à [y intégrer l’implémentation](../../error-messages/tool-errors/missing-function-body-or-variable.md) de la fonction, puis l’appeler. Pour résoudre ce problème, veillez à fournir une définition pour l’ensemble appelé déclaré des membres d’une classe.

Cette erreur peut être dû à une tentative d’appeler une fonction virtuelle pure à partir de la classe de base abstraite. Une fonction virtuelle pure n’a aucune implémentation de classe de base. Pour résoudre ce problème, assurez-vous que toutes appelées fonctions virtuelles sont implémentées.

Cette erreur peut être provoquée par essaie d’utiliser une variable déclarée dans une fonction ([une variable locale](../../error-messages/tool-errors/automatic-function-scope-variables.md)) en dehors de la portée de cette fonction. Pour résoudre ce problème, supprimez la référence à la variable qui n’est pas dans la portée, ou déplacez la variable à une étendue plus élevée.

Cette erreur peut se produire lorsque vous générez une version d’un projet ATL, de produire un message que le code de démarrage du CRT est requis. Pour résoudre ce problème, effectuez l’une des opérations suivantes,

- Supprimer `_ATL_MIN_CRT` dans la liste du préprocesseur définit pour autoriser le code de démarrage du CRT à inclure. Consultez [General Property Page (Project)](../../build/reference/general-property-page-project.md) pour plus d’informations.

- Si possible, supprimez les appels aux fonctions CRT qui nécessitent le code de démarrage du CRT. Au lieu de cela, utilisez leurs équivalents Win32. Par exemple, utilisez `lstrcmp` à la place de `strcmp`. Fonctions connues qui requièrent le code de démarrage du CRT sont certaines des fonctions à virgule flottante et chaîne.

### <a name="compilation-and-link-issues"></a>Problèmes de compilation et liaison

Cette erreur peut se produire lorsque le projet n’a pas une référence à une bibliothèque (. LIB) ou un objet (. Fichier OBJ). Pour résoudre ce problème, ajoutez une référence à la bibliothèque requise ou le fichier de l’objet à votre projet. Pour plus d’informations, consultez [fichiers .lib en tant qu’entrée de l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).

Cette erreur peut se produire si vous utilisez le [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) ou [/Zl](../../build/reference/zl-omit-default-library-name.md) options. Lorsque vous spécifiez ces options, les bibliothèques qui contiennent le code requis ne sont pas liés dans le projet, sauf si vous les avez explicitement incluses. Pour résoudre ce problème, incluez explicitement toutes les bibliothèques que vous utilisez sur la ligne de commande de lien. Si vous voyez plusieurs noms de fonction CRT ou bibliothèque Standard manquantes lorsque vous utilisez ces options, vous devez explicitement incluent les fichiers de bibliothèque et des DLL de bibliothèque Standard ou CRT dans le lien.

Si vous compilez à l’aide de la **/CLR** option, il peut y avoir une référence à .cctor manquante. Pour résoudre ce problème, consultez [l’initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md) pour plus d’informations.

Cette erreur peut se produire si vous liez aux bibliothèques de mode de mise en production lors de la création d’une version debug d’une application. De même, si vous utilisez les options **/MTd** ou **/MDd** ou définir `_DEBUG` et ensuite lier aux bibliothèques de mise en production, vous devez vous attendre à nombreux éventuels externes non résolus, entre autres problèmes. Liaison d’une génération en mode de mise en production avec les bibliothèques de débogage provoque également des problèmes similaires. Pour résoudre ce problème, assurez-vous que vous utilisez les bibliothèques de débogage dans vos versions debug, et génère des bibliothèques de vente au détail dans votre commerce de détail.

Cette erreur peut se produire si votre code fait référence à un symbole d’une version d’une bibliothèque, mais que vous fournissez une version différente de la bibliothèque à l’éditeur de liens. En règle générale, vous ne pouvez pas mélanger des fichiers objets ou bibliothèques qui sont générées pour les différentes versions du compilateur. Les bibliothèques qui font partie d’une nouvelle version peut contenir des symboles est introuvable dans les bibliothèques incluses dans les versions précédentes et vice versa. Pour résoudre ce problème, créez tous les fichiers objets et bibliothèques avec la même version du compilateur avant de les lier entre elles.

- Les outils &#124; Options &#124; projets &#124; boîte de dialogue répertoires VC ++, dans la sélection de fichiers de bibliothèque, vous permet de modifier l’ordre de recherche de bibliothèque. Le dossier de l’éditeur de liens dans la boîte de dialogue Pages de propriétés du projet peut également contenir des chemins d’accès qui peut être obsolètes.

- Ce problème peut apparaître lorsqu’un nouveau SDK est installé (par exemple pour un autre emplacement), et l’ordre de recherche n’est pas mis à jour pour pointer vers le nouvel emplacement. En règle générale, vous devez placer le chemin d’accès au nouveau SDK include et lib répertoires devant l’emplacement de Visual C++ par défaut. En outre, un projet contenant des chemins incorporés peut pointer vers d’anciens chemins qui sont valides, mais il est obsolète pour les nouvelles fonctionnalités ajoutées par la nouvelle version qui est installée dans un autre emplacement.

- Si vous générez à la ligne de commande et que vous avez créé vos propres variables d’environnement, vérifiez que les chemins d’accès aux outils, bibliothèques et fichiers d’en-tête accédez à une version cohérente. Pour plus d’informations, consultez [définir le chemin d’accès et les Variables d’environnement pour les générations de ligne de commande](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

Il n’existe actuellement aucune norme pour [d’affectation de noms C++](../../error-messages/tool-errors/name-decoration.md) entre les éditeurs de compilateurs ou même entre différentes versions d’un compilateur. Par conséquent, la liaison de fichiers objets compilés avec d’autres compilateurs ne peut pas produire le même schéma d’affectation de noms et donc causer l’erreur LNK2001.

[Options de compilation de mixage inline et non inline](../../error-messages/tool-errors/function-inlining-problems.md) sur différents modules peut causer l’erreur LNK2001. Si une bibliothèque C++ est créée avec la fonctionnalité inline activée (**/Ob1** ou **/Ob2**), mais le fichier d’en-tête correspondant décrivant les fonctions a désactivé cette fonctionnalité (aucun `inline` mot clé), cette erreur se produit. Pour résoudre ce problème, définissez les fonctions `inline` dans le fichier d’en-tête que vous incluez dans d’autres fichiers de code source.

Si vous utilisez le `#pragma inline_depth` Assurez-vous directive du compilateur que vous avez un [valeur égale ou supérieure à 2](../../error-messages/tool-errors/function-inlining-problems.md)et vérifiez que vous utilisez également le [/Ob1](../../build/reference/ob-inline-function-expansion.md) ou [/Ob2](../../build/reference/ob-inline-function-expansion.md) option du compilateur.

Cette erreur peut se produire si vous omettez le lien option /NOENTRY lorsque vous créez une DLL de ressource uniquement. Pour résoudre ce problème, ajoutez l’option /NOENTRY à la commande de lien.

Cette erreur peut se produire si vous utilisez /SUBSYSTEM incorrect ou les paramètres/Entry dans votre projet. Par exemple, si vous écrivez une application console et que vous spécifiez/SUBSYSTEM : Windows, une erreur externe non résolue est générée pour `WinMain`. Pour résoudre ce problème, assurez-vous que vous faire correspondre les options pour le type de projet. Pour plus d’informations sur ces options et les points d’entrée, consultez le [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) et [/Entry](../../build/reference/entry-entry-point-symbol.md) les options de l’éditeur de liens.

### <a name="exported-symbol-issues"></a>Problèmes de symbole exporté

Cette erreur se produit lorsqu’une exportation répertoriée dans un fichier .def est introuvable. Il peut s’agir, car il n’existe pas, est mal orthographié ou utilise des noms décorés. Un fichier .def n’accepte pas les noms décorés. Pour résoudre ce problème, supprimez les exportations inutiles et utilisez `extern "C"` déclarations pour les symboles exportés.

## <a name="what-is-an-unresolved-external-symbol"></a>Qu’est un symbole externe non résolu ?

Un *symbole* est le nom d’une fonction ou une variable globale qui sert en interne par un fichier objet compilé ou la bibliothèque. Un symbole est *défini* dans le fichier objet où le stockage est alloué pour une variable globale ou pour une fonction, où est placé le code compilé pour le corps de fonction. Un *symbole externe* est un symbole de *référencé*, autrement dit, utilisé ou appelé dans un fichier objet, mais définies dans un fichier de bibliothèque ou un objet différent. Un *exporté symbole* est celui qui est accessible publiquement par le fichier objet ou la bibliothèque qui le définit. L’éditeur de liens doit *résoudre*, ou recherchez la définition correspondante pour chaque symbole externe référencé par un fichier objet lorsqu’il est lié à une application ou une DLL. L’éditeur de liens génère une erreur lorsqu’il ne peut pas résoudre un symbole externe en recherchant un symbole exporté correspondant dans un des fichiers liés.

## <a name="use-the-decorated-name-to-find-the-error"></a>Utiliser le nom décoré pour rechercher l’erreur

L’utilisation du compilateur et éditeur de liens C++ [décoration de nom](../../error-messages/tool-errors/name-decoration.md), également appelé *substantypage*, pour encoder les informations supplémentaires sur le type d’une variable ou le type de retour, les types de paramètre, étendue et l’appel convention d’une fonction dans le nom du symbole. Ce nom décoré est le nom du symbole l’éditeur de liens recherche pour résoudre les symboles externes.

Étant donné que les informations supplémentaires deviennent une partie du nom du symbole, une erreur de lien peut entraîner si la déclaration d’une variable ou une fonction ne correspond pas exactement à la définition de la fonction ou une variable. Cela peut se produire même si le même fichier d’en-tête est utilisé dans le code appelant et le code de définition si les indicateurs de compilateur différents sont utilisés lors de la compilation des fichiers sources. Par exemple, vous pouvez obtenir cette erreur si votre code est compilé pour utiliser le `__vectorcall` convention d’appel, mais vous liez à une bibliothèque qui attend que les clients à appeler à l’aide de la valeur par défaut `__cdecl` ou `__fastcall` convention d’appel. Dans ce cas, les symboles ne correspondent pas, car les conventions d’appel sont différentes

Pour vous aider à trouver la cause de ce genre d’erreur, le message d’erreur de l’éditeur de liens vous montre les deux le « nom convivial, » le nom utilisé dans le code source et le nom décoré (entre parenthèses) pour le symbole externe non résolu. Vous n’avez pas besoin de savoir comment traduire le nom décoré pour être en mesure de le comparer avec les autres noms décorés. Vous pouvez utiliser les outils de ligne de commande qui sont inclus avec le compilateur pour comparer le nom de symbole attendu et le nom de symbole réel :

- Le [/EXPORTE](../../build/reference/dash-exports.md) et [/symboles](../../build/reference/symbols.md) options de l’outil de ligne de commande DUMPBIN peuvent vous aider à identifier les symboles sont définis dans vos fichiers .dll et objets ou bibliothèques. Vous pouvez utiliser ceci pour vérifier que le décorés exportés noms décorés l’éditeur de liens recherche les noms correspondent à.

Dans certains cas, l’éditeur de liens peut uniquement indiquer le nom décoré pour un symbole. Vous pouvez utiliser l’outil de ligne de commande UNDNAME pour obtenir la forme non décorée d’un nom décoré.

## <a name="additional-resources"></a>Ressources supplémentaires

Pour plus d’informations sur les causes et solutions pour LNK2001, consultez la question à Stack Overflow [qu’est une erreur de symbole externe non défini référence/non résolu et comment le corriger ?](http://stackoverflow.com/q/12573816/2002113).

