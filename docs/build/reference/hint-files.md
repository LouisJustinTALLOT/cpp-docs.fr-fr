---
description: 'En savoir plus sur : fichiers Hint'
title: Fichiers hint
ms.date: 02/26/2019
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: b9dc4655bde832011afcf03aa7f9a5be34807420
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191652"
---
# <a name="hint-files"></a>Fichiers hint

Un *fichier hint* contient des macros qui sinon entraîneraient l’omission de régions de code par l’Analyseur de base de données de navigation C++. Quand vous ouvrez un projet Visual Studio C++, l’analyseur analyse le code de chaque fichier source du projet et crée une base de données avec des informations sur chaque identificateur. L’IDE utilise ces informations pour prendre en charge les fonctionnalités de navigation de code, comme le navigateur **Affichage de classes** et la **Barre de navigation**.

L’Analyseur de base de données de navigation C++ est un analyseur approximatif qui peut analyser de grandes quantités de code dans un court laps de temps. Il est rapide en partie parce qu’il ignore le contenu des blocs. Par exemple, il enregistre uniquement l’emplacement et les paramètres d’une fonction et ignore son contenu. Certaines macros peuvent entraîner des problèmes de l’heuristique utilisée pour déterminer le début et la fin d’un bloc. Ces problèmes entraînent un enregistrement incorrect des régions de code.

Ces régions ignorées peuvent se manifester de plusieurs façons :

- Types et fonctions manquants dans **Affichage de classes**, **Atteindre** et la **Barre de navigation**

- Étendues incorrectes dans la **Barre de navigation**

- Suggestions pour **créer une définition/déclaration** pour les fonctions déjà définies

Un fichier hint contient des indicateurs personnalisables par l’utilisateur, qui ont la même syntaxe que les définitions de macros C/C++. Visual C++ contient un fichier hint intégré, suffisant pour la plupart des projets. Toutefois, vous pouvez créer vos propres fichiers hint pour améliorer l’analyseur pour votre projet en particulier.

> [!IMPORTANT]
> Si vous modifiez ou ajoutez un fichier hint, vous devez effectuer des étapes supplémentaires pour que les modifications prennent effet :
>
> - Dans les versions antérieures à Visual Studio 2017 version 15,6 : supprimez le fichier. sdf et/ou le fichier VC. db dans la solution pour toutes les modifications.
> - Dans Visual Studio 2017 version 15,6 et versions ultérieures : fermez et rouvrez la solution après avoir ajouté de nouveaux fichiers hint.

## <a name="scenario"></a>Scénario

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Sans fichier hint, `Function` n’apparaît pas dans **Affichage de classes**, **Atteindre** ou la **Barre de navigation**. Après l’ajout d’un fichier hint avec cette définition de macro, l’analyseur comprend et remplace la macro `NOEXCEPT`, ce qui lui permet d’analyser correctement la fonction :

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Macros provoquant des problèmes

Il existe deux catégories de macros qui perturbent l’analyseur :

- Les macros qui encapsulent les mots clés ornant une fonction

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   Pour ces types de macros, seul le nom de la macro est requis dans le fichier hint :

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Les macros qui contiennent des parenthèses non équilibrées

   ```cpp
   #define BEGIN {
   ```

   Pour ces types de macros, le nom de la macro et son contenu sont requis dans le fichier hint :

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Prise en charge de l’éditeur

À compter de Visual Studio 2017 version 15.8, plusieurs fonctionnalités permettent d’identifier les macros à problème :

- Les macros qui se trouvent dans les régions ignorées par l’analyseur sont mises en surbrillance.

- Il existe une Action rapide pour créer un fichier hint qui inclut la macro en surbrillance ou il en existe déjà un pour y ajouter la macro.

![Macro en surbrillance.](media/hint-squiggle-and-actions.png "Indice tilde et actions rapides")

Après l’exécution de l’une des Actions rapides, l’analyseur effectue une nouvelle analyse des fichiers affectés par le fichier hint.

Par défaut, la macro à problème est mise en surbrillance comme suggestion. La mise en surbrillance peut être remplacée par quelque chose de plus notable, par exemple une ligne ondulée (tilde) rouge ou verte. Utilisez l’option **Macros dans les régions ignorées par la navigation** dans la section **Tildes du code** sous **Outils** > **Options** > **Éditeur de texte** > **C/C++** > **Vue**.

![Macros dans l’option zones de navigation ignorées.](media/skipped-regions-squiggle-option.png "Option de tilde de régions ignorée.")

## <a name="display-browsing-database-errors"></a>Afficher les erreurs de la base de données de navigation

La   >  commande **de menu Afficher les erreurs de la base de données de navigation** affiche toutes les régions qui n’ont pas pu être analysées dans le **liste d’erreurs**. La commande est destinée à simplifier la génération du fichier hint initial. Toutefois, l’analyseur ne peut pas déterminer si la cause de l’erreur était une macro à problème, c’est pourquoi vous devez évaluer chaque erreur. Exécutez la commande **Afficher les erreurs de la base de données de navigation** et parcourez chaque erreur pour charger le fichier affecté dans l’éditeur. Une fois que le fichier est chargé, si des macros sont dans la région, elles sont mises en surbrillance. Vous pouvez appeler les Actions rapides pour les ajouter dans un fichier hint. Après une mise à jour du fichier hint, la liste d’erreurs est actualisée automatiquement. Sinon, si vous modifiez manuellement le fichier hint, vous pouvez utiliser la commande **Relancer l’analyse de la solution** pour déclencher une mise à jour.

## <a name="architecture"></a>Architecture

Les fichiers hint concernent des répertoires physiques, et non pas les répertoires logiques affichés dans l’**Explorateur de solutions**. Vous n’avez pas à ajouter un fichier hint dans votre projet pour que ce fichier soit pris en compte. Le système d’analyse utilise des fichiers hint seulement quand il analyse des fichiers sources.

Chaque fichier hint est nommé **cpp.hint**. Plusieurs répertoires peuvent contenir un fichier hint, mais un répertoire particulier ne peut contenir qu’un seul fichier hint.

Votre projet peut être affecté par zéro ou plusieurs fichiers hint. S’il n’existe pas de fichier hint, le système d’analyse utilise des techniques de récupération d’erreur pour ignorer le code source indéchiffrable. Sinon, le système d’analyse utilise la stratégie suivante pour rechercher et rassembler les indicateurs.

### <a name="search-order"></a>Ordre de recherche

Le système d’analyse recherche les fichiers hint dans les répertoires selon l’ordre suivant.

- Le répertoire qui contient le package d’installation pour Visual C++ (**vcpackages**). Ce répertoire contient un fichier hint intégré qui décrit les symboles des fichiers système fréquemment utilisés, comme **windows.h**. Par conséquent, votre projet hérite automatiquement de la plupart des indicateurs dont il a besoin.

- Chemin depuis le répertoire racine d’un fichier source au répertoire qui contient le fichier source lui-même. Dans un projet Visual Studio C++ classique, le répertoire racine contient le fichier projet ou solution.

   L’exception à cette règle est le cas où un *fichier stop* se trouve dans le chemin vers le fichier source. Un fichier stop est tout fichier appelé **cpp.stop**. Un fichier stop offre un contrôle supplémentaire sur l’ordre de recherche. Au lieu de démarrer du répertoire racine, le système d’analyse recherche à partir du répertoire qui contient le fichier stop jusqu’au répertoire qui contient le fichier source. Dans un projet classique, vous n’avez pas besoin d’un fichier stop.

### <a name="hint-gathering"></a>Collecte des indicateurs

Un fichier hint contient zéro à plusieurs *indicateurs*. Un indicateur est défini ou supprimé exactement comme une macro C/C++. La directive de préprocesseur `#define` crée ou redéfinit un indicateur, et la directive `#undef` le supprime.

Le système d’analyse ouvre chaque fichier hint dans l’ordre de recherche décrit précédemment. Il rassemble les indicateurs de chaque fichier dans un ensemble d’*indicateurs effectifs*, puis les utilise pour interpréter les identificateurs présents dans votre code.

Le système d’analyse utilise ces règles pour rassembler les indicateurs :

- Si le nouvel indicateur spécifie un nom qui n’est pas déjà défini, il ajoute le nom aux indicateurs effectifs.

- Si le nouvel indicateur spécifie un nom qui est déjà défini, il redéfinit l’indicateur existant.

- Si le nouvel indicateur est une directive `#undef` qui spécifie un indicateur effectif existant, il supprime l’indicateur existant.

La première règle signifie que les indicateurs effectifs sont hérités des fichiers hint précédemment ouverts. Les deux dernières règles signifient que des indicateurs arrivés plus tard dans l’ordre de recherche peuvent remplacer les indicateurs arrivés plus tôt. Par exemple, vous pouvez remplacer des indicateurs précédents si vous créez un fichier hint dans le répertoire qui contient un fichier source.

Pour une description de la collecte des indicateurs, consultez la section [Exemple](#example).

### <a name="syntax"></a>Syntaxe

Créez et supprimez des indicateurs avec la même syntaxe que les directives de préprocesseur qui créent et suppriment des macros. En fait, le système d’analyse utilise le préprocesseur C/C++ pour évaluer les indicateurs. Pour plus d’informations sur les directives de préprocesseur, consultez [#define, directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) et [#undef, directive (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md).

Les seuls éléments syntaxiques inhabituels sont les chaînes de remplacement `@<`, `@=` et `@>`. Ces chaînes de remplacement spécifiques aux fichiers hint sont utilisées seulement dans des macros de *mappage*. Un mappage est un ensemble de macros qui lient des données, des fonctions ou des événements à d’autres données, fonctions ou gestionnaires d’événements. Par exemple, `MFC` utilise des mappages pour créer des [tables des messages](../../mfc/reference/message-maps-mfc.md), et `ATL` utilise des mappages pour créer des [mappages des objets](../../atl/reference/object-map-macros.md). Les chaînes de remplacement des fichiers hint marquent les éléments de début, intermédiaires et de fin d’un mappage. Seul le nom d’une macro de mappage est significatif. Ainsi, chaque chaîne de remplacement masque intentionnellement l’implémentation de la macro.

Les indicateurs utilisent cette syntaxe :

|Syntaxe|Signification|
|------------|-------------|
|`#define` *nom de l’indicateur* *chaîne de remplacement*<br /><br /> `#define` *nom de l’indicateur* `(` *paramètre*, ...`)`*chaîne de remplacement*|Une directive de préprocesseur qui définit un nouvel indicateur ou redéfinit un indicateur existant. Après la directive, le préprocesseur remplace chaque occurrence de *nom de l’indicateur* dans le code source par *chaîne de remplacement*.<br /><br /> La deuxième forme de la syntaxe définit un indicateur de type fonction. Si un indicateur de type fonction apparaît dans le code source, le préprocesseur remplace d’abord chaque occurrence de *paramètre* dans *chaîne de remplacement* par l’argument correspondant dans le code source, puis remplace *nom de l’indicateur* par *chaîne de remplacement*.|
|`@<`|*Chaîne de remplacement* spécifique à un fichier hint qui indique le début d’un ensemble d’éléments de mappage.|
|`@=`|*Chaîne de remplacement* spécifique à un fichier hint qui indique un élément de table intermédiaire. Une table peut avoir plusieurs éléments de table.|
|`@>`|*Chaîne de remplacement* spécifique à un fichier hint qui indique la fin d’un ensemble d’éléments de mappage.|
|`#undef` *nom de l’indicateur*|Directive de préprocesseur qui supprime un indicateur existant. Le nom de l’indicateur est fourni par l’identificateur de *nom de l’indicateur*.|
|`//`*Commentaire*|Commentaire sur une seule ligne.|
|`/*`*Commentaire*`*/`|Commentaire multiligne.|

## <a name="example"></a>Exemple

Cet exemple illustre la façon dont les indicateurs sont accumulés à partir de fichiers hint. Cet exemple n’utilise pas de fichiers stop.

L’illustration montre certains des répertoires physiques d’un projet Visual Studio C++. Des fichiers hint se trouvent dans les répertoires `vcpackages`, `Debug`, `A1` et `A2`.

### <a name="hint-file-directories"></a>Répertoires des fichiers hint

![Répertoires de fichiers Hint communs et Project&#45;spécifiques.](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Répertoires et contenu des fichiers hint

Cette liste montre les répertoires de ce projet qui contiennent des fichiers hint et le contenu de ces fichiers. Seuls certains des nombreux indicateurs du fichier hint du répertoire `vcpackages` sont listés :

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- Débogage

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>Indicateurs effectifs

Ce tableau liste les indicateurs effectifs pour les fichiers sources de ce projet :

- Fichier source : A1_A2_B.cpp

- Indicateurs effectifs :

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

Ces remarques s’appliquent à la liste précédente :

- Les indicateurs effectifs proviennent des répertoires `vcpackages`, `Debug`, `A1` et `A2`.

- La directive **#undef** dans le fichier hint `Debug` a supprimé l’indicateur `#define _In_` dans le fichier hint du répertoire `vcpackages`.

- Le fichier hint du répertoire `A1` redéfinit `START_NAMESPACE`.

- L’indicateur `#undef` dans le répertoire `A2` a supprimé les indicateurs pour `OBRACE` et `CBRACE` dans le fichier hint du répertoire `Debug`.

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual Studio C++](file-types-created-for-visual-cpp-projects.md)<br>
[#define, directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef, directive (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Annotations SAL](../../c-runtime-library/sal-annotations.md)<br>
