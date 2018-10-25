---
title: 'Recordset : Création et fermeture de Recordsets (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4da86f43cf89720132aba0eaa611a01a3902fb1a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059023"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Recordset : création et fermeture de recordsets (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Pour utiliser un jeu d’enregistrements, construisez un objet recordset et appelez sa `Open` fonction membre pour exécuter la requête du recordset et sélectionner des enregistrements. Lorsque vous avez terminé avec le jeu d’enregistrements, fermez et détruire l’objet.

Cette rubrique explique :

- [Quand et comment créer un objet recordset](#_core_creating_recordsets_at_run_time).

- [Quand et comment vous pouvez qualifier le comportement du recordset en paramétrant, le filtrage, de tri ou le verrouillant](#_core_setting_recordset_options).

- [Quand et comment fermer un objet recordset](#_core_closing_a_recordset).

##  <a name="_core_creating_recordsets_at_run_time"></a> Création de jeux d’enregistrements en cours d’exécution

Avant de pouvoir créer des objets de jeu d’enregistrements dans votre programme, vous écrivez généralement les classes de jeu d’enregistrements spécifiques à l’application. Pour plus d’informations sur cette étape préliminaire, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Ouvrir un objet de feuille de réponse dynamique ou instantané lorsque vous avez besoin sélectionner des enregistrements à partir d’une source de données. Le type d’objet à créer dépend de ce que vous devez faire avec les données dans votre application et sur quels votre pilote ODBC prend en charge. Pour plus d’informations, consultez [Dynaset](../../data/odbc/dynaset.md) et [instantané](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Pour ouvrir un jeu d’enregistrements

1. Construisez un objet de votre `CRecordset`-classe dérivée.

   Vous pouvez construire l’objet sur le tas ou sur le frame de pile d’une fonction.

1. Vous pouvez éventuellement modifier le comportement de jeu d’enregistrements par défaut. Pour les options disponibles, consultez [définition des Options de jeu d’enregistrements](#_core_setting_recordset_options).

1. Appeler l’objet [Open](../../mfc/reference/crecordset-class.md#open) fonction membre.

Dans le constructeur, passez un pointeur vers un `CDatabase` de l’objet ou passer NULL pour utiliser un objet de base de données temporaire que l’infrastructure construit et ouvre en fonction de la chaîne de connexion retournée par la [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) fonction membre. Le `CDatabase` objet peut déjà être connecté à une source de données.

L’appel à `Open` utilise SQL pour sélectionner des enregistrements à partir de la source de données. Le premier enregistrement sélectionné (le cas échéant) est l’enregistrement actif. Les valeurs des champs de cet enregistrement sont stockées dans les membres de données de champ de l’objet recordset. Si tous les enregistrements ont été sélectionnés, à la fois le `IsBOF` et `IsEOF` fonctions membres retournent 0.

Dans votre [Open](../../mfc/reference/crecordset-class.md#open) appel, vous pouvez :

- Spécifiez si le recordset est une feuille de réponse dynamique ou un instantané. Par défaut, les jeux d’enregistrements sont ouverts en tant que captures instantanées. Ou bien, vous pouvez spécifier un jeu d’enregistrements avant uniquement, ce qui ne permet que le défilement avant, un seul enregistrement à la fois.

   Par défaut, un jeu d’enregistrements utilise le type par défaut stocké dans le `CRecordset` membre de données `m_nDefaultType`. Assistants écrivent du code pour initialiser `m_nDefaultType` pour le type de jeu d’enregistrements que vous choisissez dans l’Assistant. Au lieu d’accepter cette valeur par défaut, vous pouvez remplacer un autre type de jeu d’enregistrements.

- Spécifiez une chaîne pour remplacer la valeur par défaut SQL **sélectionnez** instruction construit le jeu d’enregistrements.

- Spécifiez si le jeu d’enregistrements est en lecture seule ou en mode append-only. Autorise les jeux d’enregistrements complet de la mise à jour par défaut, mais vous pouvez limiter que pour l’ajout de nouveaux enregistrements uniquement ou vous pouvez interdire toutes les mises à jour.

L’exemple suivant montre comment ouvrir un objet instantané en lecture seule de la classe `CStudentSet`, une classe spécifique à l’application :

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Après avoir appelé `Open`, utilisez les membres de données et des fonctions de membre de l’objet pour travailler avec les enregistrements. Dans certains cas, vous souhaiterez actualiser ou actualiser le jeu d’enregistrements pour inclure les modifications qui se sont produites sur la source de données. Pour plus d’informations, consultez [Recordset : actualisant un Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  La chaîne de connexion que vous utilisez pendant le développement n’est peut-être pas la même chaîne de connexion nécessitant les utilisateurs finaux. Pour trouver des idées sur la généralisation de votre application à cet égard, consultez [Source de données : gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="_core_setting_recordset_options"></a> Définition des Options de jeu d’enregistrements

Après avoir construit votre objet recordset, mais avant d’appeler `Open` pour sélectionner des enregistrements, vous souhaiterez peut-être définir des options pour contrôler le comportement du recordset. Pour tous les jeux d’enregistrements, vous pouvez :

- Spécifiez un [filtre](../../data/odbc/recordset-filtering-records-odbc.md) pour contraindre la sélection d’enregistrement.

- Spécifiez un [tri](../../data/odbc/recordset-sorting-records-odbc.md) afin que les enregistrements.

- Spécifiez [paramètres](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) afin de pouvoir sélectionner des enregistrements à l’aide des informations fournies ou calculées au moment de l’exécution.

Vous pouvez également définir l’option suivante si certaines conditions sont remplies :

- Si le jeu d’enregistrements est modifiable et prend en charge les options de verrouillage, spécifiez la [verrouillage](../../data/odbc/recordset-locking-records-odbc.md) méthode utilisée pour les mises à jour.

> [!NOTE]
>  Pour affecter la sélection d’enregistrement, vous devez définir ces options avant d’appeler le `Open` fonction membre.

##  <a name="_core_closing_a_recordset"></a> Fermeture d’un Recordset

Lorsque vous avez terminé avec votre jeu d’enregistrements, vous devez supprimer et désallouer sa mémoire.

#### <a name="to-close-a-recordset"></a>Pour fermer un jeu d’enregistrements

1. Appeler son [fermer](../../mfc/reference/crecordset-class.md#close) fonction membre.

1. Détruire l’objet recordset.

   Si vous l’avez déclarée sur le frame de pile d’une fonction, l’objet est détruit automatiquement lorsque l’objet est hors de portée. Sinon, utilisez le **supprimer** opérateur.

`Close` Libère le jeu d’enregistrements `HSTMT` gérer. Elle ne supprime pas l’objet C++.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)