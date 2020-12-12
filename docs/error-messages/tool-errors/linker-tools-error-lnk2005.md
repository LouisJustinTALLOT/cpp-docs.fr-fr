---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2005'
title: Erreur des outils Éditeur de liens LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: c6de300bc731104f51056911515d0cc7a95e05f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338494"
---
# <a name="linker-tools-error-lnk2005"></a>Erreur des outils Éditeur de liens LNK2005

> *symbole* déjà défini dans l’objet

Le *symbole* Symbol a été défini plusieurs fois.

Cette erreur est suivie de l’erreur irrécupérable [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

En général, cette erreur signifie que vous avez endommagé la *règle de définition unique*, qui n’autorise qu’une seule définition pour un modèle, une fonction, un type ou un objet utilisé dans un fichier objet donné, et une seule définition sur l’exécutable entier pour des objets ou des fonctions visibles de l’extérieur.

Voici quelques causes courantes de cette erreur.

- Cette erreur peut se produire lorsqu’un fichier d’en-tête définit une variable. Par exemple, si vous incluez ce fichier d’en-tête dans plusieurs fichiers sources de votre projet, une erreur est générée :

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Voici les solutions possibles :

  - Déclarez la variable **`extern`** dans le fichier d’en-tête : `extern int global_int;` , puis définissez-la et, éventuellement, initialisez-la dans un seul fichier source : `int global_int = 17;` . Cette variable est désormais un global que vous pouvez utiliser dans n’importe quel fichier source en le déclarant **`extern`** , par exemple, en incluant le fichier d’en-tête. Nous recommandons cette solution pour les variables qui doivent être globales, mais une bonne pratique d’ingénierie logicielle réduit les variables globales.

  - Déclarez la variable [static](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;` . Cela restreint la portée de la définition au fichier objet actuel et permet à plusieurs fichiers objet d’avoir leur propre copie de la variable. Nous vous déconseillons de définir des variables statiques dans les fichiers d’en-tête en raison du risque de confusion avec les variables globales. Préférez déplacer les définitions de variables statiques dans les fichiers sources qui les utilisent.

  - Déclarez la variable [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;` . Cela indique à l’éditeur de liens de choisir une définition à utiliser par toutes les références externes et d’ignorer le reste. Cette solution est parfois utile lors de la combinaison de bibliothèques d’importation. Dans le cas contraire, nous ne le recommandons pas pour éviter les erreurs de l’éditeur de liens.

- Cette erreur peut se produire lorsqu’un fichier d’en-tête définit une fonction qui n’est pas **`inline`** . Si vous incluez ce fichier d’en-tête dans plusieurs fichiers sources, vous recevez plusieurs définitions de la fonction dans l’exécutable.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Voici les solutions possibles :

  - Ajoutez le **`inline`** mot clé à la fonction :

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Supprimez le corps de la fonction du fichier d’en-tête et laissez uniquement la déclaration, puis implémentez la fonction dans un seul fichier source :

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- Cette erreur peut également se produire si vous définissez des fonctions membres en dehors de la déclaration de classe dans un fichier d’en-tête :

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Pour résoudre ce problème, déplacez les définitions des fonctions membres à l’intérieur de la classe. Les fonctions membres définies dans une déclaration de classe sont implicitement Inline.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Cette erreur peut se produire si vous liez plusieurs versions de la bibliothèque standard ou de la bibliothèque CRT. Par exemple, si vous tentez de lier les bibliothèques CRT de vente au détail et de débogage, ou à la fois les versions statiques et dynamiques d’une bibliothèque, ou deux versions différentes d’une bibliothèque standard à votre fichier exécutable, cette erreur peut être signalée plusieurs fois. Pour résoudre ce problème, supprimez toutes les copies sauf une pour chaque bibliothèque de la commande Link. Nous vous déconseillons de combiner des bibliothèques de vente au détail et de débogage, ou des versions différentes d’une bibliothèque, dans le même exécutable.

   Pour indiquer à l’éditeur de liens d’utiliser des bibliothèques autres que les valeurs par défaut, sur la ligne de commande, spécifiez les bibliothèques à utiliser et utilisez l’option [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pour désactiver les bibliothèques par défaut. Dans l’IDE, ajoutez des références à votre projet pour spécifier les bibliothèques à utiliser, puis ouvrez la boîte de dialogue **pages de propriétés** pour votre projet et, dans l' **éditeur de liens**, page de propriétés **d’entrée** , définissez soit **Ignorer toutes les bibliothèques par défaut**, soit ignorer les propriétés de **bibliothèques par défaut spécifiques** pour désactiver les bibliothèques par défaut.

- Cette erreur peut se produire si vous combinez l’utilisation de bibliothèques statiques et dynamiques lorsque vous utilisez l’option [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . Par exemple, cette erreur peut se produire si vous générez une DLL à utiliser dans votre fichier exécutable qui est lié à la bibliothèque CRT statique. Pour résoudre ce problème, utilisez uniquement des bibliothèques statiques ou des bibliothèques dynamiques pour l’exécutable entier et pour toutes les bibliothèques que vous générez pour l’utiliser dans l’exécutable.

- Cette erreur peut se produire si le symbole est une fonction packagée (créée en compilant avec [/Gy](../../build/reference/gy-enable-function-level-linking.md)) et qu’il a été inclus dans plusieurs fichiers, mais a été modifié entre les compilations. Pour résoudre ce problème, recompilez tous les fichiers qui incluent la fonction empaquetée.

- Cette erreur peut se produire si le symbole est défini différemment dans deux objets membres dans des bibliothèques différentes, et si les deux objets membres sont utilisés. Une façon de résoudre ce problème lorsque les bibliothèques sont liées de manière statique consiste à utiliser l’objet membre à partir d’une seule bibliothèque, et à inclure cette bibliothèque d’abord sur la ligne de commande de l’éditeur de liens. Pour utiliser les deux symboles, vous devez créer un moyen de les distinguer. Par exemple, si vous pouvez générer les bibliothèques à partir de la source, vous pouvez encapsuler chaque bibliothèque dans un espace de noms unique. Vous pouvez également créer une bibliothèque de wrappers qui utilise des noms uniques pour encapsuler les références à l’une des bibliothèques d’origine, lier la nouvelle bibliothèque à la bibliothèque d’origine, puis lier l’exécutable à votre nouvelle bibliothèque au lieu de la bibliothèque d’origine.

- Cette erreur peut se produire si une `extern const` variable est définie deux fois et a une valeur différente dans chaque définition. Pour résoudre ce problème, définissez la constante une seule fois, ou utilisez des espaces **`enum class`** de noms ou des définitions pour distinguer les constantes.

- Cette erreur peut se produire si vous utilisez UUID. lib conjointement avec d’autres fichiers. lib qui définissent des GUID (par exemple, OleDb. lib et adsiid. lib). Par exemple :

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Pour résoudre ce problème, ajoutez [/force : multiple](../../build/reference/force-force-file-output.md) aux options de ligne de commande de l’éditeur de liens et assurez-vous que UUID. lib est la première bibliothèque référencée.
