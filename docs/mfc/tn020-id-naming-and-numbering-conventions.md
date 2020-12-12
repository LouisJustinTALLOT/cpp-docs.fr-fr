---
description: 'En savoir plus sur : TN020 : conventions de dénomination des ID et de numérotation'
title: "TN020 : conventions de dénomination d'ID et de numérotation"
ms.date: 11/04/2016
f1_keywords:
- vc.id
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
ms.openlocfilehash: 85f59e45ec9d4ce748515cf638f4fb4cf33c7d38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215870"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020 : conventions de dénomination d'ID et de numérotation

Cette note décrit les conventions d’attribution de noms et de numérotation d’ID utilisées par MFC 2,0 pour les ressources, les commandes, les chaînes, les contrôles et les fenêtres enfants.

Les conventions d’attribution de noms et de numérotation des ID MFC sont destinées à répondre aux exigences suivantes :

- Fournissez une norme de nom d’ID cohérente utilisée dans la bibliothèque MFC et les applications MFC prises en charge par l’éditeur de ressources de Visual C++. Cela permet au programmeur d’interpréter plus facilement le type et l’origine d’une ressource à partir de son ID.

- Insistez sur la forte relation 1-à-1 entre certains types d’ID.

- Se conformer aux normes déjà largement utilisées pour l’attribution de noms aux ID dans Windows.

- Partitionner l’espace de numérotation d’ID. Les numéros d’identification peuvent être affectés par les ressources de programmeur, MFC, Windows et Visual C++ modifiées. Le partitionnement approprié permet d’éviter la duplication des numéros d’identification.

## <a name="the-id-prefix-naming-convention"></a>Convention d’affectation de noms de préfixe d’ID

Plusieurs types d’ID peuvent se produire dans une application. La Convention d’attribution de noms MFC ID définit des préfixes différents pour différents types de ressources.

MFC utilise le préfixe « IDR_ » pour indiquer un ID de ressource qui s’applique à plusieurs types de ressources. Par exemple, pour une fenêtre frame donnée, MFC utilise le même préfixe « IDR_ » pour indiquer une ressource de menu, d’accélérateur, de chaîne et d’icône. Le tableau suivant présente les différents préfixes et leur utilisation :

|Préfixe|Utilisation|
|------------|---------|
|IDR_|Pour plusieurs types de ressources (principalement utilisés pour les menus, les accélérateurs et les rubans).|
|IDD_|Pour les ressources de modèle de boîte de dialogue (par exemple, IDD_DIALOG1).|
|IDC_|Pour les ressources de curseur.|
|IDI_|Pour les ressources d’icône.|
|IDB_|Pour les ressources bitmap.|
|IDS_|Pour les ressources de type chaîne.|

Dans une ressource de boîte de dialogue, MFC respecte les conventions suivantes :

|Préfixe ou étiquette|Utilisation|
|---------------------|---------|
|IDOK, IDCANCEL|Pour les ID de bouton de commande standard.|
|IDC_|Pour les autres contrôles de boîte de dialogue.|

Le préfixe « IDC_ » est également utilisé pour les curseurs. Ce conflit de noms n’est généralement pas un problème, car une application classique aura peu de curseurs et de nombreux contrôles de boîte de dialogue.

Dans une ressource de menu, MFC respecte les conventions suivantes :

|Préfixe|Utilisation|
|------------|---------|
|IDM_|Pour les éléments de menu qui n’utilisent pas l’architecture de commande MFC.|
|ID_|Pour les commandes de menu qui utilisent l’architecture de commande MFC.|

Les commandes qui suivent l’architecture de commande MFC doivent avoir un gestionnaire de commandes ON_COMMAND et peuvent avoir un gestionnaire de ON_UPDATE_COMMAND_UI. Si ces gestionnaires de commandes suivent l’architecture de commande MFC, ils fonctionneront correctement s’ils sont liés à une commande de menu, un bouton de barre d’outils ou un bouton de barre de boîte de dialogue. Le même préfixe « ID_ » est également utilisé pour une chaîne d’invite de menu qui s’affiche dans la barre des messages du programme. La plupart des éléments de menu de votre application doivent respecter les conventions de commande MFC. Tous les ID de commande standard (par exemple, ID_FILE_NEW) suivent cette Convention.

MFC utilise également « IDP_ » comme forme spécialisée de chaînes (au lieu de « IDS_ »). Les chaînes avec le préfixe « IDP_ » sont des invites, c’est-à-dire des chaînes utilisées dans les boîtes de message. Les chaînes « IDP_ » peuvent contenir « %1 » et « %2 » comme espaces réservés des chaînes déterminées par le programme. Les chaînes « IDP_ » sont généralement associées à des rubriques d’aide et les chaînes « IDS_ » ne le sont pas. Les chaînes « IDP_ » sont toujours localisées et les chaînes « IDS_ » peuvent ne pas être localisées.

La bibliothèque MFC utilise également le préfixe « IDW_ » comme forme spécialisée d’ID de contrôle (au lieu de « IDC_ »). Ces ID sont assignés aux fenêtres enfants, telles que les vues et les séparateurs, par les classes d’infrastructure. Les ID d’implémentation MFC ont pour préfixe « AFX_ ».

## <a name="the-id-numbering-convention"></a>Convention de ID-Numbering

Le tableau suivant répertorie les plages valides pour les ID des types spécifiques. Certaines limites sont des limites d’implémentation technique, tandis que d’autres sont des conventions conçues pour empêcher vos ID d’entrer en conflit avec des ID prédéfinis Windows ou des implémentations par défaut MFC.

Nous vous recommandons vivement de définir tous les ID à l’intérieur des plages recommandées. La limite inférieure de ces plages est 1, car 0 n’est pas utilisé. Nous vous recommandons d’utiliser la Convention commune et d’utiliser 100 ou 101 comme premier ID.

|Préfixe|Type de ressource|Plage valide|
|------------|-------------------|-----------------|
|IDR_|multiple|1 à 0x6FFF|
|IDD_|modèles de boîte de dialogue|1 à 0x6FFF|
|IDC_, IDI_ IDB_|curseurs, icônes, bitmaps|1 à 0x6FFF|
|IDS_, IDP_|chaînes générales|1 à 0x7FFF|
|ID_|commandes|0x8000 à 0xDFFF|
|IDC_|controls|8 à 0xDFFF|

Les raisons de ces limites de plage sont les suivantes :

- Par Convention, la valeur d’ID 0 n’est pas utilisée.

- Les limitations de l’implémentation Windows limitent les véritables ID de ressource à une valeur inférieure ou égale à 0x7FFF.

- L’infrastructure interne de MFC réserve ces plages :

  - 0x7000 via 0x7FFF (voir AFXRES. h)

  - 0xE000 via 0xEFFF (voir AFXRES. h)

  - de 16000 à 18000 (voir afxribbonres. h)

  Ces plages peuvent changer dans les futures implémentations MFC.

- Plusieurs commandes système Windows utilisent la plage de 0xF000 à 0xFFFF.

- Les ID de contrôle de 1 à 7 sont réservés aux contrôles standard tels que IDOK et IDCANCEL.

- La plage de 0x8000 à 0xFFFF pour les chaînes est réservée aux invites de menu pour les commandes.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
