---
description: 'En savoir plus sur : Comment : gérer les symboles'
title: 'Comment : gérer des symboles'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 2a7bdc6994bfcdadc9b7d1d5b98350fcd47ad6fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118223"
---
# <a name="how-to-manage-symbols"></a>Comment : gérer des symboles

Lorsque vous créez une ressource ou un objet de ressource, l’environnement de développement lui assigne un nom de symbole par défaut, par exemple `IDD_DIALOG1` . Vous pouvez utiliser la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour modifier le nom de symbole par défaut ou pour modifier le nom d’un symbole déjà associé à une ressource.

Pour les symboles associés à une ressource unique, vous pouvez également utiliser la fenêtre **Propriétés** pour modifier la valeur du symbole. Vous pouvez utiliser la [boîte de dialogue symboles des ressources](./creating-new-symbols.md) pour modifier la valeur des symboles qui ne sont pas actuellement assignés à une ressource.

Normalement, toutes les définitions de symbole sont enregistrées dans `Resource.h` . Toutefois, vous devrez peut-être changer ce nom de fichier Include pour pouvoir, par exemple, utiliser plusieurs fichiers de ressources dans le même répertoire.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier. RC, consultez [Comment : créer des ressources](how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Restrictions relatives au nom de symbole

Les restrictions relatives aux noms de symboles sont les suivantes :

- Tous les [symboles](symbols-resource-identifiers.md) doivent être uniques dans l’étendue de l’application pour empêcher les définitions de symbole conflictuelles dans les fichiers d’en-tête.

- Les caractères valides pour un nom de symbole incluent A-Z, a-z, 0-9 et les traits de soulignement (_).

- Les noms de symboles ne peuvent pas commencer par un chiffre et sont limités à 247 caractères.

- Les noms de symboles ne peuvent pas contenir d’espaces.

- Les noms de symboles ne respectent pas la casse, mais la casse de la première définition de symbole est préservée.

   Le fichier d'en-tête qui définit les symboles est utilisé par le compilateur/l'éditeur de ressources, ainsi que par le ou les programmes C++ pour faire référence aux ressources définies dans un fichier de ressources. Quand deux noms de symboles diffèrent uniquement par la casse, le programme C++ identifie deux symboles distincts alors que le compilateur/l'éditeur de ressources identifie les deux noms comme faisant référence à un symbole unique.

> [!NOTE]
> Si vous ne suivez pas le schéma de nom de symbole standard (ID * _ [Keyword]) présenté ci-dessous et que le nom de votre symbole est le même qu’un mot clé connu du compilateur de script de ressources, la tentative de génération du fichier de script de ressources entraîne une génération d’erreurs apparemment aléatoires difficile à diagnostiquer. Pour éviter cela, respectez le modèle d'affectation de noms standard.

Les noms de symboles comportent des préfixes descriptifs qui indiquent le genre de ressource ou d'objet qu'ils représentent. Ces préfixes descriptifs commencent par la combinaison de texte ID. La bibliothèque MFC (Microsoft Foundation Class) utilise les conventions d’affectation des noms de symboles indiquées dans le tableau suivant :

|Category|Préfixe|Utilisation|
|--------------|------------|---------|
|Ressources|IDR_, IDD_, IDC_, IDI_, IDB_|Accélérateur ou menu (et ressources associées ou personnalisées), boîte de dialogue, curseur, icône, bitmap|
|Éléments de menu|ID_|Élément de menu|
|Commandes|ID_|Commande|
|Contrôles et fenêtres enfants|IDC_|Control|
|Chaînes|IDS_|Chaîne dans la table de chaînes|
|MFC|AFX_|Réservé aux symboles MFC prédéfinis|

### <a name="to-change-a-symbol-name-id"></a>Pour modifier un nom de symbole (ID)

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), sélectionnez la ressource.

1. Dans la fenêtre **Propriétés** , tapez un nouveau nom de symbole ou sélectionnez-en un dans la liste des symboles existants dans la zone **ID** .

   Si vous tapez un nouveau nom de symbole, une valeur lui est automatiquement affectée.

> [!NOTE]
> Vous pouvez utiliser la [boîte de dialogue symboles des ressources](./creating-new-symbols.md) pour modifier les noms des symboles qui ne sont pas actuellement assignés à une ressource.

## <a name="symbol-value-restrictions"></a>Restrictions relatives à la valeur d'un symbole

Une valeur de symbole peut être tout entier exprimé de manière normale pour les `#define` directives de préprocesseur. Voici quelques exemples de valeurs de symboles :

```
18
4001
0x0012
-3456
```

Les valeurs de symboles pour les ressources telles que les accélérateurs, les bitmaps, les curseurs, les boîtes de dialogue, les icônes, les menus, les tables de chaînes et les informations sur la version doivent être des nombres décimaux compris entre 0 et 32 767, mais ne peuvent pas être hexadécimaux. Les valeurs de symboles de certaines ressources, telles que les contrôles de boîte de dialogue ou des chaînes spécifiques de la table de chaînes, peuvent être comprises entre 0 et 65 534 ou -32 768 et 32 767. Pour plus d’informations sur les plages de nombres, consultez [TN023 : ressources MFC standard](../mfc/tn023-standard-mfc-resources.md).

Les symboles de ressource sont des nombres de 16 bits. Vous pouvez les entrer comme étant signés ou non signés, mais ils sont utilisés en interne en tant qu’entiers non signés, de sorte que les nombres négatifs sont convertis en leur valeur positive correspondante.

Certaines limitations des valeurs de symbole sont les suivantes :

- L'environnement de développement Visual Studio et MFC utilisent certaines plages de nombres à des fins spéciales. Tous les nombres avec le bit le plus significatif défini (de -32 768 à -1 ou de 32 768 à 65 534, en fonction du signe) sont réservés par MFC.

- Vous ne pouvez pas définir une valeur de symbole à l’aide d’autres chaînes de symboles. Par exemple, la définition de symbole suivante n’est pas prise en charge :

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Vous ne pouvez pas utiliser de macros de préprocesseur avec des arguments comme définitions de valeur. L’exemple suivant n’est pas une expression valide, quelle que soit la `ID` valeur de au moment de la compilation :

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- Votre application peut comporter un fichier existant contenant des symboles définis par des expressions.

### <a name="to-change-a-symbol-value"></a>Pour modifier une valeur de symbole

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), sélectionnez la ressource.

1. Dans la fenêtre **Propriétés** , tapez le nom du symbole suivi d’un signe égal et d’un entier dans la zone **ID** , par exemple :

    ```
    IDC_EDITNAME=5100
    ```

   La nouvelle valeur est stockée dans le fichier d'en-tête de symbole la prochaine fois que vous enregistrez le projet. Seul le nom du symbole reste visible dans la zone ID et le signe égal et la valeur ne sont pas affichés une fois qu’ils sont validés.

## <a name="change-or-delete-symbols"></a>Modifier ou supprimer des symboles

Dans la [boîte de dialogue symboles des ressources](./creating-new-symbols.md), vous pouvez modifier ou supprimer des symboles existants qui ne sont pas déjà attribués à une ressource ou un objet.

### <a name="to-change-an-unassigned-symbol"></a>Pour modifier un symbole non assigné

1. Dans la zone **nom** , sélectionnez le symbole non assigné, puis choisissez **modifier**.

1. Modifiez le nom ou la valeur du symbole dans les zones fournies dans la boîte de dialogue **modifier le symbole** .

> [!NOTE]
> Pour modifier un symbole affecté à une ressource ou un objet, vous devez utiliser l’éditeur de ressources ou la fenêtre **Propriétés** .

### <a name="to-delete-an-unassigned-unused-symbol"></a>Pour supprimer un symbole non assigné (non utilisé)

Dans la boîte de dialogue **symboles des ressources** , sélectionnez le symbole que vous souhaitez supprimer, puis choisissez **supprimer**.

> [!NOTE]
> Avant de supprimer un symbole inutilisé dans un fichier de ressources, assurez-vous qu’il n’est pas utilisé ailleurs dans le programme ou par les fichiers de ressources inclus au moment de la compilation.

## <a name="include-symbols"></a>Inclure les symboles

La première fois que l'environnement de développement lit un fichier de ressources créé par une autre application, il marque tous les fichiers d'en-tête inclus en lecture seule. Bien que vous puissiez utiliser la [boîte de dialogue Include des ressources](./how-to-include-resources-at-compile-time.md) pour ajouter d’autres fichiers d’en-tête de symbole en lecture seule.

Si vous envisagez de partager des fichiers de symboles entre plusieurs projets, vous pouvez utiliser les définitions de symbole en lecture seule.

Vous pouvez également utiliser des fichiers de symboles inclus quand vous disposez de ressources avec des définitions de symbole qui utilisent des expressions au lieu d'entiers simples pour définir la valeur du symbole. Par exemple :

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

L'environnement interprète correctement ces symboles calculés tant que les conditions suivantes sont respectées :

- Les symboles calculés sont placés dans un fichier de symboles en lecture seule.

- Votre fichier de ressources contient des ressources auxquelles ces symboles calculés sont déjà assignés.

- Une expression numérique est attendue.

> [!NOTE]
> Si une chaîne ou une expression numérique est attendue, l'expression n'est pas évaluée.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Pour inclure des symboles partagés (en lecture seule) dans votre fichier de ressources

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur votre fichier *. RC* , puis sélectionnez [include des ressources](./how-to-include-resources-at-compile-time.md).

1. Dans la zone **directives de symbole en lecture seule** , utilisez la `#include` directive du compilateur pour spécifier le fichier dans lequel vous souhaitez conserver les symboles en lecture seule.

   N’appelez pas le fichier `Resource.h` , car il s’agit du nom de fichier normalement utilisé par le fichier d’en-tête de symbole principal.

   > [!NOTE]
   > Ce que vous tapez dans la zone **directives de symbole en lecture seule** est inclus dans le fichier de ressources exactement comme vous le tapez. Vérifiez que ce que vous tapez ne contient aucune erreur d'orthographe ou de syntaxe.

   Utilisez la zone **directives de symbole en lecture seule** pour inclure uniquement les fichiers avec des définitions de symbole. N’incluez pas les définitions de ressources, sinon les définitions de ressource en double seront créées lors de l’enregistrement du fichier.

1. Placez les symboles dans le fichier spécifié.

   Les symboles des fichiers inclus de cette façon sont évalués chaque fois que vous ouvrez votre fichier de ressources, mais ils ne sont pas remplacés sur le disque lorsque vous enregistrez votre fichier.

1. Sélectionnez **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Pour changer le nom du fichier d'en-tête de symbole de ressource

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur votre fichier *. RC* et choisissez [include des ressources](./how-to-include-resources-at-compile-time.md).

1. Dans la zone **fichier d’en-tête de symbole** , tapez le nouveau nom du fichier include.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Identificateurs de ressource (symboles)](symbols-resource-identifiers.md)<br/>
[Comment : créer des symboles](creating-new-symbols.md)<br/>
[ID de symboles prédéfinis](predefined-symbol-ids.md)<br/>
