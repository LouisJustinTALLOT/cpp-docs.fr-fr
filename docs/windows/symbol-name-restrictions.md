---
title: Restrictions relatives au nom de symbole
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.restrictions.name
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
ms.openlocfilehash: 7b6d8804dc7f3c9768dc9e86fde0e708f67c43fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624852"
---
# <a name="symbol-name-restrictions"></a>Restrictions relatives au nom de symbole

Les restrictions relatives aux noms de symboles sont les suivantes :

- Tous les [symboles](../windows/symbols-resource-identifiers.md) doit être unique dans l’étendue de l’application. Cela empêche les conflits de définitions de symbole dans les fichiers d'en-tête.

- Les caractères valides pour un nom de symbole incluent A-Z, a-z, 0-9 et les traits de soulignement (_).

- Les noms de symboles ne peuvent pas commencer par un chiffre. Par ailleurs, ils sont limités à 247 caractères.

- Les noms de symboles ne peuvent pas contenir d'espaces.

- Les noms de symboles ne respectent pas la casse. Toutefois, la casse de la première définition de symbole est conservée. Le fichier d'en-tête qui définit les symboles est utilisé par le compilateur/l'éditeur de ressources, ainsi que par le ou les programmes C++ pour faire référence aux ressources définies dans un fichier de ressources. Quand deux noms de symboles diffèrent uniquement par la casse, le programme C++ identifie deux symboles distincts alors que le compilateur/l'éditeur de ressources identifie les deux noms comme faisant référence à un symbole unique.

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

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Modification d’un symbole ou d’un nom de symbole (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Restrictions relatives à la valeur d’un symbole](../windows/symbol-value-restrictions.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)