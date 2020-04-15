---
title: 'Recordset : création et fermeture de recordsets (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 41b1c11e2c820b6e5777e1af426c5e1253ed5468
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367077"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Recordset : création et fermeture de recordsets (ODBC)

> [!NOTE]
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez toujours créer un consommateur manuellement.

Cette rubrique s’applique aux classes ODBC MFC.

Pour utiliser un recordset, construisez un objet recordset et appelez sa fonction membre `Open` pour exécuter la requête du recordset et sélectionner des enregistrements. Quand vous n’avez plus besoin du recordset, fermez et détruisez l’objet.

Cette rubrique répond aux questions suivantes :

- [Quand et comment créer un objet recordset](#_core_creating_recordsets_at_run_time).

- [Quand et comment qualifier le comportement du recordset en le paramétrant, le filtrant, le triant ou le verrouillant](#_core_setting_recordset_options).

- [Quand et comment fermer un objet recordset](#_core_closing_a_recordset).

## <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a> Création de recordsets au moment de l’exécution

Pour pouvoir créer des objets recordset dans votre programme, vous écrivez généralement des classes recordset propres à l’application. Pour plus d’informations sur cette étape préliminaire, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Ouvrez un objet de feuille de réponse dynamique ou d’instantané quand vous avez besoin de sélectionner des enregistrements d’une source de données. Le type d’objet à créer dépend de ce que vous devez faire avec les données de votre application et de ce que votre pilote ODBC prend en charge. Pour plus d’informations, consultez [Feuille de réponse dynamique](../../data/odbc/dynaset.md) et [Instantané](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Pour ouvrir un recordset

1. Construisez un objet de votre classe dérivée `CRecordset`.

   Vous pouvez construire l’objet sur le tas ou sur le frame de pile d’une fonction.

1. Vous pouvez éventuellement modifier le comportement du recordset par défaut. Pour connaître les options disponibles, consultez [Définition des options de recordset](#_core_setting_recordset_options).

1. Appelez la fonction membre [Open](../../mfc/reference/crecordset-class.md#open) de l’objet.

Dans le constructeur, passez un pointeur à un objet `CDatabase` ou passez NULL pour utiliser un objet de base de données temporaire que le framework construit et ouvre en fonction de la chaîne de connexion retournée par la fonction membre [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect). L’objet `CDatabase` est peut-être déjà connecté à une source de données.

L’appel à `Open` utilise SQL pour sélectionner des enregistrements de la source de données. Le premier enregistrement sélectionné (le cas échéant) est l’enregistrement actuel. Les valeurs des champs de cet enregistrement sont stockées dans les membres de données de champ de l’objet recordset. Si tous les enregistrements ont été sélectionnés, les fonctions membres `IsBOF` et `IsEOF` retournent toutes les deux 0.

Dans votre appel à [Open](../../mfc/reference/crecordset-class.md#open), vous pouvez :

- Spécifiez si le recordset est une feuille de réponse dynamique ou un instantané. Par défaut, les recordsets s’ouvrent comme des instantanés. Sinon, vous pouvez spécifier un recordset de type avant uniquement, ce qui permet uniquement le défilement avant, un seul enregistrement à la fois.

   Par défaut, un recordset utilise le type par défaut stocké dans le membre de données `m_nDefaultType` de `CRecordset`. Les Assistants écrivent du code pour initialiser `m_nDefaultType` sur le type de recordset que vous choisissez dans l’Assistant. Au lieu d’accepter cette valeur par défaut, vous pouvez la remplacer par un autre type de recordset.

- Spécifiez une chaîne pour remplacer l’instruction SQL **SELECT** par défaut construite par le recordset.

- Spécifiez si le recordset est en lecture seule ou en ajout uniquement. Les recordsets autorisent une mise à jour complète par défaut, mais vous pouvez limiter la mise à jour à l’ajout de nouveaux enregistrements uniquement ou vous pouvez interdire toutes les mises à jour.

L’exemple suivant montre comment ouvrir un objet d’instantané en lecture seule de la classe `CStudentSet`, une classe propre à l’application :

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Après avoir appelé `Open`, utilisez les fonctions membres et les membre de données de l’objet pour utiliser les enregistrements. Dans certains cas, vous pouvez réinterroger ou actualiser le recordset pour introduire les changements qui se sont produits au niveau de la source de données. Pour plus d’informations, voir [Recordset: Requerying a Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
> La chaîne de connexion que vous utilisez pendant le développement peut ne pas être la même que celle dont vos utilisateurs finaux ont besoin. Pour des idées sur la généralisation de votre application à cet égard, voir [Source de données: Gérer les connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

## <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a> Définition des options de recordset

Après avoir construit votre objet recordset, mais avant d’appeler `Open` pour sélectionner des enregistrements, vous pouvez définir des options pour contrôler le comportement du recordset. Pour tous les recordsets, vous pouvez :

- Spécifier un [filtre](../../data/odbc/recordset-filtering-records-odbc.md) pour contraindre la sélection d’enregistrement.

- Spécifier un ordre de [tri](../../data/odbc/recordset-sorting-records-odbc.md) pour les enregistrements.

- Spécifier des [paramètres](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) afin de pouvoir sélectionner des enregistrements à l’aide des informations fournies ou calculées au moment de l’exécution.

Vous pouvez également définir l’option suivante si les conditions sont remplies :

- Si le recordset est modifiable et prend en charge les options de verrouillage, spécifiez la méthode de [verrouillage](../../data/odbc/recordset-locking-records-odbc.md) utilisée pour les mises à jour.

> [!NOTE]
> Pour affecter la sélection d’enregistrements, vous devez définir ces options avant d’appeler la fonction membre `Open`.

## <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a> Fermeture d’un recordset

Quand vous n’avez plus besoin de votre recordset, vous devez le supprimer et désallouer sa mémoire.

#### <a name="to-close-a-recordset"></a>Pour fermer un recordset

1. Appelez sa fonction membre [Close](../../mfc/reference/crecordset-class.md#close).

1. Détruisez l’objet recordset.

   Si vous l’avez déclaré sur le frame de pile d’une fonction, l’objet est détruit automatiquement quand il est hors de portée. Sinon, utilisez l’opérateur **delete**.

`Close` libère le handle `HSTMT` du recordset. Il ne détruit pas l’objet C++.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Recordset : ajout, modification et suppression d'enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
