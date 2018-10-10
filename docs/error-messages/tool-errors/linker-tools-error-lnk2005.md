---
title: Erreur LNK2005 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3dbb1d63e7d7c6f5e036fc0cde967277c91a40
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890125"
---
# <a name="linker-tools-error-lnk2005"></a>Erreur des outils Éditeur de liens LNK2005

> *symbole* déjà définie dans l’objet

Le symbole *symbole* a été défini plusieurs fois.

Cette erreur est suivie d’une erreur irrécupérable [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

En règle générale, cette erreur signifie que vous avez interrompu le *règle d’unique définition*, ce qui ne permet qu’une seule définition pour n’importe quel modèle utilisé, une fonction, un type ou un objet dans un fichier de l’objet donné et qu’une seule définition dans l’exécutable tout entier pour les objets visibles de l’extérieur ou fonctions.

Voici certaines causes courantes de cette erreur.

- Cette erreur peut se produire lorsqu’un fichier d’en-tête définit une variable. Par exemple, si vous incluez ce fichier d’en-tête dans plusieurs fichiers source dans votre projet, une erreur se produit :

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Plusieurs solutions sont possibles :

   - Déclarez la variable `extern` dans le fichier d’en-tête : `extern int global_int;`, puis de le définir et éventuellement l’initialiser dans un seul et unique fichier source : `int global_int = 17;`. Cette variable est désormais un global que vous pouvez utiliser dans n’importe quel fichier source en le déclarant `extern`, par exemple, en incluant le fichier d’en-tête. Nous vous recommandons cette solution pour les variables qui doivent être globales, mais d’ingénierie logicielle bonne pratique réduit les variables globales.

   - Déclarez la variable [statique](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`. Cela limite l’étendue de la définition dans le fichier objet en cours et autorise plusieurs fichiers objet possèdent leur propre copie de la variable. Nous ne recommandons pas que définir de variables statiques dans les fichiers d’en-tête en raison du risque de confusion avec les variables globales. Vous souhaitez déplacer les définitions de variables statiques dans les fichiers sources qui les utilisent.

   - Déclarez la variable [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. Ce code indique à l’éditeur de liens pour sélectionner une définition pour une utilisation par toutes les références externes et ignorer le reste. Cette solution est parfois utile lors de la combinaison des bibliothèques d’importation. Sinon, nous déconseillons il possible pour éviter les erreurs de l’éditeur de liens.

- Cette erreur peut se produire lorsqu’un fichier d’en-tête définit une fonction qui n’est pas `inline`. Si vous incluez ce fichier d’en-tête dans plusieurs fichiers source, vous obtenez plusieurs définitions de la fonction dans le fichier exécutable.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Plusieurs solutions sont possibles :

   - Ajouter le `inline` mot clé à la fonction :

        ```h
        // LNK2005_func_inline.h
        inline int sample_function(int k) { return 42 * (k % 167); }
        ```

   - Supprimer le corps de fonction à partir du fichier d’en-tête et laisser uniquement la déclaration, puis implémentez la fonction dans un seul et unique fichier source :

        ```h
        // LNK2005_func_decl.h
        int sample_function(int);
        ```

        ```cpp
        // LNK2005_func_impl.cpp
        int sample_function(int k) { return 42 * (k % 167); }
        ```

- Cette erreur peut également se produire si vous définissez les fonctions de membre en dehors de la déclaration de classe dans un fichier d’en-tête :

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Pour résoudre ce problème, déplacez les définitions de fonction membre à l’intérieur de la classe. Les fonctions membres définies à l’intérieur d’une déclaration de classe sont implicitement inline.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Cette erreur peut se produire si vous liez plusieurs versions de la bibliothèque standard ou CRT. Par exemple, si vous tentez de lier à la fois la vente au détail et les bibliothèques de débogage CRT ou les deux versions d’une bibliothèque statiques et dynamiques, ou deux versions différentes d’une bibliothèque standard pour votre fichier exécutable, cette erreur peut apparaître plusieurs fois. Pour résoudre ce problème, supprimez tout sauf une copie de chaque bibliothèque à partir de la commande de lien. Nous ne recommandons pas de mélanger la vente au détail et de débogage des bibliothèques ou des versions différentes d’une bibliothèque, dans le même exécutable.

   Pour indiquer à l’éditeur de liens à utiliser des bibliothèques autres que les valeurs par défaut, sur la ligne de commande, spécifiez les bibliothèques pour utiliser et utiliser le [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) option pour désactiver les bibliothèques par défaut. Dans l’IDE, ajouter des références à votre projet pour spécifier les bibliothèques à utiliser, puis ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet et dans le **l’éditeur de liens**, **entrée** propriété Définissez soit **ignorer de toutes les bibliothèques par défaut**, ou **bibliothèques par défaut spécifiques ignorées** propriétés pour désactiver les bibliothèques par défaut.

- Cette erreur peut se produire si vous combinez des bibliothèques statiques et dynamiques lorsque vous utilisez le [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) option. Par exemple, cette erreur peut se produire si vous générez une DLL à utiliser dans votre fichier exécutable que les liens dans la bibliothèque CRT statique. Pour résoudre ce problème, utilisez uniquement les bibliothèques statiques ou des bibliothèques dynamiques pour l’ensemble de l’exécutable et pour toutes les bibliothèques que vous générez pour l’utiliser dans le fichier exécutable.

- Cette erreur peut se produire si le symbole est une fonction packagée (créée par compilation avec [/Gy](../../build/reference/gy-enable-function-level-linking.md)) et il a été inclus dans plusieurs fichiers, mais a été modifié entre les compilations. Pour résoudre ce problème, recompilez tous les fichiers qui incluent la fonction packagée.

- Cette erreur peut se produire si le symbole est défini différemment dans deux objets membres de bibliothèques différentes, et les deux objets membres sont utilisés. Une façon de résoudre ce problème lorsque les bibliothèques sont liées statiquement consiste à utiliser l’objet de membre à partir de la bibliothèque qu’une seule et inclure cette bibliothèque tout d’abord sur la ligne de commande de l’éditeur de liens. Pour utiliser les deux symboles, vous devez créer un moyen pour les distinguer. Par exemple, si vous pouvez générer les bibliothèques à partir de la source, vous pouvez encapsuler chaque bibliothèque dans un espace de noms unique. Vous pouvez également créer une nouvelle bibliothèque de wrapper qui utilise des noms uniques pour encapsuler des références à une des bibliothèques d’origine, de lier la nouvelle bibliothèque à la bibliothèque d’origine, puis de lier le fichier exécutable à votre nouvelle bibliothèque au lieu de la bibliothèque d’origine.

- Cette erreur peut se produire si un `extern const` variable est définie à deux reprises et a une valeur différente dans chaque définition. Pour résoudre ce problème, définir la constante qu’une seule fois, ou utiliser des espaces de noms ou `enum class` définitions pour distinguer les constantes.

- Cette erreur peut se produire si vous utilisez uuid.lib en association avec d’autres fichiers .lib qui définissent des identificateurs GUID (par exemple, oledb.lib et adsiid.lib). Exemple :

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Pour résoudre ce problème, ajoutez [multiple](../../build/reference/force-force-file-output.md) pour les options de ligne de commande de l’éditeur de liens et assurez-vous que uuid.lib est la première bibliothèque référencée.
