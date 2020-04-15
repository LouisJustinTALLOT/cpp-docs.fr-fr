---
title: Erreur des outils Éditeur de liens LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 6090478c3761c477250b6706a350e261b51f2a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353239"
---
# <a name="linker-tools-error-lnk2005"></a>Erreur des outils Éditeur de liens LNK2005

> *symbole* déjà défini dans l’objet

Le *symbole* a été défini plus d’une fois.

Cette erreur est suivie d’une erreur fatale [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

En général, cette erreur signifie que vous avez enfreint la *règle d’une définition*, qui ne permet qu’une seule définition pour tout modèle, fonction, type ou objet utilisé dans un fichier d’objet donné, et une seule définition dans l’ensemble exécutable pour des objets ou fonctions visibles de l’extérieur.

Voici quelques causes courantes de cette erreur.

- Cette erreur peut se produire lorsqu’un fichier d’en-tête définit une variable. Par exemple, si vous incluez ce fichier d’en-tête dans plus d’un fichier source dans votre projet, une erreur se traduit par :

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Voici les solutions possibles :

  - Déclarez `extern` la variable dans `extern int global_int;`le fichier d’en-tête: , puis définissez-la et paraally dans un et unique fichier source: `int global_int = 17;`. Cette variable est maintenant un global que vous pouvez `extern`utiliser dans n’importe quel fichier source en le déclarant, par exemple, en incluant le fichier d’en-tête. Nous recommandons cette solution pour les variables qui doivent être globales, mais une bonne pratique d’ingénierie logicielle minimise les variables mondiales.

  - Déclarez [static](../../cpp/storage-classes-cpp.md#static)la `static int static_int = 17;`variable statique : . Cela limite la portée de la définition au fichier d’objet actuel et permet à plusieurs fichiers d’objets d’avoir leur propre copie de la variable. Nous ne vous recommandons pas de définir les variables statiques dans les fichiers d’en-tête en raison du risque de confusion avec les variables globales. Préférez déplacer des définitions variables statiques dans les fichiers sources qui les utilisent.

  - Déclarez [selectany](../../cpp/selectany.md)la sélection `__declspec(selectany) int global_int = 17;`variable : . Cela indique au linker de choisir une définition pour une utilisation par toutes les références externes et de jeter le reste. Cette solution est parfois utile lors de la combinaison des bibliothèques d’importation. Sinon, nous ne le recommandons pas comme un moyen d’éviter les erreurs de liaison.

- Cette erreur peut se produire lorsqu’un fichier `inline`d’en-tête définit une fonction qui ne l’est pas. Si vous incluez ce fichier d’en-tête dans plus d’un fichier source, vous obtenez plusieurs définitions de la fonction dans l’exécutable.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Voici les solutions possibles :

  - Ajouter `inline` le mot clé à la fonction :

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Retirez le corps de la fonction du fichier d’en-tête et ne laissez que la déclaration, puis implémentez la fonction dans un seul et unique fichier source :

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- Cette erreur peut également se produire si vous définissez les fonctions des membres en dehors de la déclaration de classe dans un fichier d’en-tête :

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Pour résoudre ce problème, déplacez les définitions de fonction du membre à l’intérieur de la classe. Les fonctions des membres définies à l’intérieur d’une déclaration de classe sont implicitement inlinées.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Cette erreur peut se produire si vous liez plus d’une version de la bibliothèque standard ou CRT. Par exemple, si vous essayez de lier à la fois les bibliothèques CRT de détail et de débopt, ou les versions statiques et dynamiques d’une bibliothèque, ou deux versions différentes d’une bibliothèque standard à votre exécutable, cette erreur peut être signalée plusieurs fois. Pour résoudre ce problème, supprimez toutes les copies sauf une de chaque bibliothèque de la commande de lien. Nous ne vous recommandons pas de mélanger les bibliothèques de vente au détail et de débopt, ou différentes versions d’une bibliothèque, dans la même exécutoire.

   Pour dire au linker d’utiliser des bibliothèques autres que les par défaut, sur la ligne de commande, spécifiez les bibliothèques à utiliser et utilisez l’option [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pour désactiver les bibliothèques par défaut. Dans l’IDE, ajoutez des références à votre projet pour spécifier les bibliothèques à utiliser, puis ouvrez le dialogue **des pages de propriété** pour votre projet, et dans la page de propriété **Linker,** **Input,** définissez soit **Ignorez toutes les bibliothèques par défaut,** soit **ignorez les** propriétés spécifiques des bibliothèques par défaut pour désactiver les bibliothèques par défaut.

- Cette erreur peut se produire si vous mélangez l’utilisation de bibliothèques statiques et dynamiques lorsque vous utilisez [l’option /clr.](../../build/reference/clr-common-language-runtime-compilation.md) Par exemple, cette erreur peut se produire si vous construisez un DLL pour une utilisation dans votre exécutable qui relie dans le CRT statique. Pour résoudre ce problème, n’utilisez que des bibliothèques statiques ou uniquement des bibliothèques dynamiques pour l’ensemble exécutable et pour toutes les bibliothèques que vous construisez pour utiliser dans l’exécutable.

- Cette erreur peut se produire si le symbole est une fonction emballée (créée par la compilation avec [/Gy](../../build/reference/gy-enable-function-level-linking.md)) et qu’elle a été incluse dans plus d’un fichier, mais a été modifiée entre les compilations. Pour résoudre ce problème, recomposer tous les fichiers qui incluent la fonction emballée.

- Cette erreur peut se produire si le symbole est défini différemment dans deux objets membres dans différentes bibliothèques, et les deux objets membres sont utilisés. Une façon de résoudre ce problème lorsque les bibliothèques sont statiquement liées est d’utiliser l’objet membre d’une seule bibliothèque, et d’inclure cette bibliothèque d’abord sur la ligne de commande de liaison. Pour utiliser les deux symboles, vous devez créer un moyen de les distinguer. Par exemple, si vous pouvez construire les bibliothèques à partir de la source, vous pouvez envelopper chaque bibliothèque dans un espace de nom unique. Alternativement, vous pouvez créer une nouvelle bibliothèque d’emballage qui utilise des noms uniques pour envelopper les références à l’une des bibliothèques d’origine, relier la nouvelle bibliothèque à la bibliothèque d’origine, puis lier l’exécutable à votre nouvelle bibliothèque au lieu de la bibliothèque d’origine.

- Cette erreur peut `extern const` se produire si une variable est définie deux fois, et a une valeur différente dans chaque définition. Pour résoudre ce problème, définissez la constante une `enum class` seule fois, ou utilisez des espaces de noms ou des définitions pour distinguer les constantes.

- Cette erreur peut se produire si vous utilisez uuid.lib en combinaison avec d’autres fichiers .lib qui définissent les GUIDs (par exemple, oledb.lib et adsiid.lib). Par exemple :

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Pour résoudre ce problème, ajoutez [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) aux options de ligne de commande de liaison, et assurez-vous que uuid.lib est la première bibliothèque référencée.
