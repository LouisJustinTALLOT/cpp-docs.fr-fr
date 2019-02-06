---
title: Modification d’un symbole
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
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
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 7d2890c2d2c05f1ee0309446dfe2de9917f85707
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763984"
---
# <a name="changing-a-symbol"></a>Modification d’un symbole

Quand vous créez une ressource ou un objet de ressource, l'environnement de développement lui assigne un nom de symbole par défaut, par exemple, IDD_DIALOG1. Vous pouvez utiliser la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour modifier le nom du symbole par défaut ou modifier le nom d’un symbole déjà associé à une ressource.

Pour les symboles associés à une seule ressource, vous pouvez également utiliser le **propriétés** fenêtre pour modifier la valeur du symbole. Vous pouvez utiliser la [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md) pour modifier la valeur des symboles pas actuellement assignés à une ressource. Pour plus d’informations, consultez [modification des symboles non assignés](../windows/changing-unassigned-symbols.md).

Normalement toutes les définitions de symbole sont enregistrées dans `Resource.h`. Toutefois, vous devrez peut-être changer ce nom de fichier Include pour pouvoir, par exemple, utiliser plusieurs fichiers de ressources dans le même répertoire.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

## <a name="to-change-a-resources-symbol-name-id"></a>Pour modifier le nom de symbole d’une ressource (ID)

1. Dans [affichage des ressources](../windows/resource-view-window.md), sélectionnez la ressource.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le **propriétés** fenêtre, tapez un nouveau nom de symbole ou sélectionnez dans la liste des symboles existants dans le **ID** boîte.

   Si vous tapez un nouveau nom de symbole, il reçoit automatiquement une valeur.

Vous pouvez utiliser la [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md) pour modifier les noms de symboles pas actuellement assignés à une ressource. Pour plus d’informations, consultez [modification des symboles non assignés](../windows/changing-unassigned-symbols.md).

### <a name="symbol-name-restrictions"></a>Restrictions de nom de symbole

Les restrictions relatives aux noms de symboles sont les suivantes :

- Tous les [symboles](../windows/symbols-resource-identifiers.md) doit être unique dans l’étendue de l’application. Cela empêche les conflits de définitions de symbole dans les fichiers d'en-tête.

- Les caractères valides pour un nom de symbole incluent A-Z, a-z, 0-9 et les traits de soulignement (_).

- Les noms de symboles ne peuvent pas commencer par un chiffre. Par ailleurs, ils sont limités à 247 caractères.

- Les noms de symboles ne peuvent pas contenir d'espaces.

- Les noms de symboles ne respectent pas la casse. Toutefois, la casse de la première définition de symbole est conservée. Le fichier d'en-tête qui définit les symboles est utilisé par le compilateur/l'éditeur de ressources, ainsi que par le ou les programmes C++ pour faire référence aux ressources définies dans un fichier de ressources. Quand deux noms de symboles diffèrent uniquement par la casse, le programme C++ identifie deux symboles distincts alors que le compilateur/l'éditeur de ressources identifie les deux noms comme faisant référence à un symbole unique.

   > [!NOTE]
   > Si vous ne suivez pas le modèle de nom de symbole standard (ID*_[keyword]) décrit ci-dessous, et si votre nom de symbole est identique à un mot clé connu du compilateur de script de ressources, la génération du fichier de script de ressources entraînera des erreurs aléatoires difficiles à diagnostiquer. Pour éviter cela, respectez le modèle d'affectation de noms standard.

Les noms de symboles comportent des préfixes descriptifs qui indiquent le genre de ressource ou d'objet qu'ils représentent. Ces préfixes descriptifs commencent par la combinaison de texte ID. La bibliothèque MFC (Microsoft Foundation Class) utilise les conventions d'affectation de noms de symboles illustrées dans le tableau suivant.

|Catégorie|Préfixe|Utilisez|
|--------------|------------|---------|
|Ressources|IDR_ IDD_ IDC_ IDI_ IDB_|Accélérateur ou menu (et ressources associées ou personnalisées), boîte de dialogue, curseur, icône, image bitmap|
|Éléments de menu|ID_|Menu Item|
|Commandes|ID_|Commande|
|Contrôles et fenêtres enfants|IDC_|Contrôle|
|Chaînes|IDS_|Chaîne dans la table de chaînes|
|MFC|AFX_|Réservé aux symboles MFC prédéfinis|

## <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Pour modifier une valeur de symbole assignée à une ressource ou un objet unique

1. Dans [affichage des ressources](../windows/resource-view-window.md), sélectionnez la ressource.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le **propriétés** fenêtre, tapez le nom du symbole suivi par un signe égal et d’un entier dans la **ID** zone, par exemple :

    ```
    IDC_EDITNAME=5100
    ```

La nouvelle valeur est stockée dans le fichier d'en-tête de symbole la prochaine fois que vous enregistrez le projet. Seul le nom du symbole reste visible dans la zone ID. Le signe égal et la valeur ne sont pas affichés après leur validation.

### <a name="symbol-value-restrictions"></a>Restrictions de valeur de symbole

Une valeur de symbole peut être un entier exprimé de façon normale pour les directives de préprocesseur #define. Voici quelques exemples de valeurs de symboles :

```
18
4001
0x0012
-3456
```

Les valeurs de symboles des ressources (accélérateurs, images bitmap, curseurs, boîtes de dialogue, icônes, menus, tables de chaînes et informations de version) doivent être des nombres décimaux compris entre 0 et 32 767 (mais en aucun cas des valeurs hexadécimales). Les valeurs de symboles de certaines ressources, telles que les contrôles de boîte de dialogue ou des chaînes spécifiques de la table de chaînes, peuvent être comprises entre 0 et 65 534 ou -32 768 et 32 767.

Les symboles des ressources sont des nombres de 16 bits. Vous pouvez les entrer en tant que nombres signés ou non signés. Toutefois, ils sont utilisés de façon interne en tant qu'entiers non signés. Les nombres négatifs sont castés en leur valeur positive correspondante.

Voici quelques limitations des valeurs de symboles :

- L'environnement de développement Visual Studio et MFC utilisent certaines plages de nombres à des fins spéciales. Tous les nombres avec le bit le plus significatif défini (de -32 768 à -1 ou de 32 768 à 65 534, en fonction du signe) sont réservés par MFC.

- Vous ne pouvez pas définir une valeur de symbole à l'aide d'autres chaînes de symboles. Par exemple, la définition de symbole suivante n'est pas prise en charge :

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Vous ne pouvez pas utiliser de macros de préprocesseur avec des arguments en tant que définitions de valeur. Exemple :

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   n'est pas une expression valide, quelle que soit la valeur de `ID` au moment de la compilation.

- Votre application peut comporter un fichier existant contenant des symboles définis par des expressions. Pour plus d’informations sur la façon d’inclure les symboles en tant que symboles en lecture seule, consultez [symboles à l’aide de partagés (lecture seule) ou calculés](../windows/including-shared-read-only-or-calculated-symbols.md).

Pour plus d’informations sur les plages numériques, consultez [TN023 : Ressources MFC standard](../mfc/tn023-standard-mfc-resources.md).

## <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Pour changer le nom du fichier d'en-tête de symbole de ressource

1. Dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur votre fichier .rc et choisissez [Include des ressources](../windows/resource-includes-dialog-box.md) dans le menu contextuel.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le **fichier d’en-tête de symbole** , tapez le nouveau nom pour le fichier include.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>
[Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)<br/>
