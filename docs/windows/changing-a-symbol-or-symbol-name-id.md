---
title: 'Procédure : Gérer les symboles'
ms.date: 11/04/2016
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
ms.openlocfilehash: 4bc0376b6b5ff402f0cc9f40093e000763ad6656
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226369"
---
# <a name="how-to-manage-symbols"></a>Procédure : Gérer les symboles

Quand vous créez une ressource ou un objet de ressource, l'environnement de développement lui assigne un nom de symbole par défaut, par exemple, IDD_DIALOG1. Vous pouvez utiliser la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour modifier le nom du symbole par défaut ou modifier le nom d’un symbole déjà associé à une ressource.

Pour les symboles associés à une seule ressource, vous pouvez également utiliser le **propriétés** fenêtre pour modifier la valeur du symbole. Vous pouvez utiliser la [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md) pour modifier la valeur des symboles pas actuellement assignés à une ressource.

Normalement toutes les définitions de symbole sont enregistrées dans `Resource.h`. Toutefois, vous devrez peut-être changer ce nom de fichier Include pour pouvoir, par exemple, utiliser plusieurs fichiers de ressources dans le même répertoire.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [création d’un fichier de Script de ressources](../windows/how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Restrictions de nom de symbole

Les restrictions relatives aux noms de symboles sont les suivantes :

- Tous les [symboles](../windows/symbols-resource-identifiers.md) doit être unique dans l’étendue de l’application. Cela empêche les conflits de définitions de symbole dans les fichiers d'en-tête.

- Les caractères valides pour un nom de symbole incluent A-Z, a-z, 0-9 et les traits de soulignement (_).

- Les noms de symboles ne peuvent pas commencer par un chiffre et sont limités à 247 caractères.

- Les noms de symboles ne peuvent pas contenir d’espaces.

- Les noms de symboles ne sont pas la casse, mais la casse de la définition du symbole est conservée. Le fichier d'en-tête qui définit les symboles est utilisé par le compilateur/l'éditeur de ressources, ainsi que par le ou les programmes C++ pour faire référence aux ressources définies dans un fichier de ressources. Quand deux noms de symboles diffèrent uniquement par la casse, le programme C++ identifie deux symboles distincts alors que le compilateur/l'éditeur de ressources identifie les deux noms comme faisant référence à un symbole unique.

   > [!NOTE]
   > Si vous ne suivez pas le modèle de nom de symbole standard (ID*_[keyword]) décrit ci-dessous, et si votre nom de symbole est identique à un mot clé connu du compilateur de script de ressources, la génération du fichier de script de ressources entraînera des erreurs aléatoires difficiles à diagnostiquer. Pour éviter cela, respectez le modèle d'affectation de noms standard.

Les noms de symboles comportent des préfixes descriptifs qui indiquent le genre de ressource ou d'objet qu'ils représentent. Ces préfixes descriptifs commencent par la combinaison de texte ID. La bibliothèque MFC (Microsoft Foundation Class) utilise les conventions d'affectation de noms de symboles illustrées dans le tableau suivant.

|Category|Préfixe|Utilisez|
|--------------|------------|---------|
|Ressources|IDR_ IDD_ IDC_ IDI_ IDB_|Accélérateur ou menu (et ressources associées ou personnalisées), boîte de dialogue, curseur, icône, image bitmap|
|Éléments de menu|ID_|Menu Item|
|Commandes|ID_|Commande|
|Contrôles et fenêtres enfants|IDC_|Contrôle|
|Chaînes|IDS_|Chaîne dans la table de chaînes|
|MFC|AFX_|Réservé aux symboles MFC prédéfinis|

### <a name="to-change-a-symbol-name-id"></a>Pour modifier un nom de symbole (ID)

1. Dans [affichage des ressources](../windows/resource-view-window.md), sélectionnez la ressource.

1. Dans le **propriétés** fenêtre, tapez un nouveau nom de symbole ou sélectionnez dans la liste des symboles existants dans le **ID** boîte.

   Si vous tapez un nouveau nom de symbole, il lui est affectée automatiquement une valeur.

Vous pouvez utiliser la [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md) pour modifier les noms de symboles pas actuellement assignés à une ressource.

## <a name="symbol-value-restrictions"></a>Restrictions de valeur de symbole

Une valeur de symbole peut être un entier exprimé de façon normale pour les directives de préprocesseur #define. Voici quelques exemples de valeurs de symboles :

```
18
4001
0x0012
-3456
```

Les valeurs de symboles des ressources (accélérateurs, images bitmap, curseurs, boîtes de dialogue, icônes, menus, tables de chaînes et informations de version) doivent être des nombres décimaux compris entre 0 et 32 767 (mais en aucun cas des valeurs hexadécimales). Les valeurs de symboles de certaines ressources, telles que les contrôles de boîte de dialogue ou des chaînes spécifiques de la table de chaînes, peuvent être comprises entre 0 et 65 534 ou -32 768 et 32 767.

Symboles des ressources sont des nombres de 16 bits. Vous pouvez les entrer en tant que signés ou non signés, toutefois, ils sont utilisés en interne sous forme d’entiers non signés. Les nombres négatifs sont castés en leur valeur positive correspondante.

Voici quelques limitations des valeurs de symboles :

- L'environnement de développement Visual Studio et MFC utilisent certaines plages de nombres à des fins spéciales. Tous les nombres avec le bit le plus significatif défini (de -32 768 à -1 ou de 32 768 à 65 534, en fonction du signe) sont réservés par MFC.

- Vous ne pouvez pas définir une valeur de symbole à l’aide d’autres chaînes de symbole. Par exemple, la définition de symbole suivante n’est pas pris en charge :

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Vous ne pouvez pas utiliser des macros de préprocesseur avec des arguments en tant que définitions de valeur. Exemple :

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   n’est pas une expression valide quelle `ID` a la valeur au moment de la compilation.

- Votre application peut comporter un fichier existant contenant des symboles définis par des expressions. Pour plus d’informations sur la façon d’inclure les symboles en tant que symboles en lecture seule, consultez [symboles à l’aide de partagés (lecture seule) ou calculés](../windows/including-shared-read-only-or-calculated-symbols.md).

Pour plus d’informations sur les plages numériques, consultez [TN023 : Ressources MFC standard](../mfc/tn023-standard-mfc-resources.md).

### <a name="to-change-a-symbol-value"></a>Pour modifier une valeur de symbole

1. Dans [affichage des ressources](../windows/resource-view-window.md), sélectionnez la ressource.

1. Dans le **propriétés** fenêtre, tapez le nom du symbole suivi par un signe égal et d’un entier dans la **ID** zone, par exemple :

    ```
    IDC_EDITNAME=5100
    ```

La nouvelle valeur est stockée dans le fichier d'en-tête de symbole la prochaine fois que vous enregistrez le projet. Uniquement le nom du symbole reste visible dans la zone ID ; le signe égal et la valeur ne sont pas affichées une fois qu’ils sont validés.

## <a name="change-or-delete-unassigned-symbols"></a>Modifier ou supprimer les symboles non assignés

Lorsque vous êtes dans le [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md), vous pouvez modifier ou supprimer les symboles existants qui ne sont pas déjà affectés à une ressource ou un objet.

### <a name="to-change-an-unassigned-symbol"></a>Pour modifier un symbole non assigné

1. Dans le **nom** zone, sélectionnez le symbole non assigné et choisissez **modification**.

1. Modifier le nom du symbole ou une valeur dans les zones fournies dans le **modifier le symbole** boîte de dialogue.

   > [!NOTE]
   > Pour changer un symbole qui *est* affecté à une ressource ou un objet, vous devez utiliser l’éditeur de ressources ou **propriétés** fenêtre.

### <a name="to-delete-an-unassigned-unused-symbol"></a>Pour supprimer un symbole non assigné (non utilisé)

Dans le [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md), sélectionnez le symbole que vous souhaitez supprimer, puis choisissez **supprimer**.

   > [!NOTE]
   > Avant de supprimer un symbole inutilisé dans un fichier de ressources, assurez-vous qu'il n'est pas utilisé ailleurs dans le programme, ni par les fichiers de ressources inclus au moment de la compilation.

## <a name="include-shared-read-only-or-calculated-symbols"></a>Inclure partagés (lecture seule) ou calculés des symboles

La première fois que l'environnement de développement lit un fichier de ressources créé par une autre application, il marque tous les fichiers d'en-tête inclus en lecture seule. Bien que vous pouvez utiliser la [boîte de dialogue Include des ressources](../windows/resource-includes-dialog-box.md) pour ajouter des fichiers d’en-tête de symbole en lecture seule.

Si vous envisagez de partager des fichiers de symboles entre plusieurs projets, vous pouvez utiliser les définitions de symbole en lecture seule.

Vous pouvez également utiliser des fichiers de symboles inclus quand vous disposez de ressources avec des définitions de symbole qui utilisent des expressions au lieu d'entiers simples pour définir la valeur du symbole. Exemple :

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

1. Dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur votre fichier .rc et choisissez [Include des ressources](../windows/resource-includes-dialog-box.md) dans le menu contextuel.

1. Dans le **directives de symboles en lecture seule** zone, utilisez la `#include` directive de compilateur pour spécifier le fichier dans lequel les symboles en lecture seule peuvent être conservées.

   N’appelez pas le fichier `Resource.h`, puisque c’est le nom de fichier utilisé normalement par le fichier d’en-tête de symbole principal.

   > [!NOTE]
   > **Important** ce que vous tapez dans la zone directives de symbole en lecture seule est inclus dans le fichier de ressources exactement comme vous le tapez. Vérifiez que ce que vous tapez ne contient aucune erreur d'orthographe ou de syntaxe.

   Utilisez le **directives de symboles en lecture seule** case pour inclure les fichiers contenant uniquement les définitions de symbole. N’incluez pas les définitions de ressource ; Sinon, les définitions de ressource en double seront créées lorsque le fichier est enregistré.

1. Placez les symboles dans le fichier spécifié.

   Les symboles dans les fichiers inclus de cette façon sont évalués chaque fois que vous ouvrez votre fichier de ressources, mais ils ne sont pas remplacés sur le disque lorsque vous enregistrez votre fichier.

1. Sélectionnez **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Pour changer le nom du fichier d'en-tête de symbole de ressource

1. Dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur votre fichier .rc et choisissez [Include des ressources](../windows/resource-includes-dialog-box.md) dans le menu contextuel.

1. Dans le **fichier d’en-tête de symbole** , tapez le nouveau nom pour le fichier include.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>
[Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)<br/>