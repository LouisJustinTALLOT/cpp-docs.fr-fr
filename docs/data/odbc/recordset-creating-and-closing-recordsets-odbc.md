---
title: "Recordset : Création et fermeture de Recordsets (ODBC) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ec09c08aa4730c11960d675aef68c8a1007c900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Recordset : création et fermeture de recordsets (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Pour utiliser un jeu d’enregistrements, construisez un objet recordset, puis appelez ses **ouvrir** fonction membre pour exécuter la requête du recordset et sélectionner des enregistrements. Lorsque vous avez terminé avec le jeu d’enregistrements, fermez et détruire l’objet.  
  
 Cette rubrique explique :  
  
-   [Quand et comment créer un objet recordset](#_core_creating_recordsets_at_run_time).  
  
-   [Quand et comment vous pouvez qualifier le comportement du recordset en paramétrant, le filtrage, de tri ou de verrouillage](#_core_setting_recordset_options).  
  
-   [Quand et comment fermer un objet recordset](#_core_closing_a_recordset).  
  
##  <a name="_core_creating_recordsets_at_run_time"></a>Création de jeux d’enregistrements en cours d’exécution  
 Avant de pouvoir créer des objets recordset dans votre programme, vous écrivez généralement les classes de jeu d’enregistrements spécifiques à l’application. Pour plus d’informations sur cette étape préliminaire, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Ouvrir un objet de feuille de réponse dynamique ou instantané lorsque vous avez besoin sélectionner des enregistrements à partir d’une source de données. Le type d’objet à créer dépend de ce que vous devez faire avec les données dans votre application et sur quel votre pilote ODBC prend en charge. Pour plus d’informations, consultez [Dynaset](../../data/odbc/dynaset.md) et [instantané](../../data/odbc/snapshot.md).  
  
#### <a name="to-open-a-recordset"></a>Pour ouvrir un jeu d’enregistrements  
  
1.  Construire un objet de votre `CRecordset`-classe dérivée.  
  
     Vous pouvez construire l’objet sur le segment de mémoire ou sur le frame de pile d’une fonction.  
  
2.  Vous pouvez modifier le comportement du jeu d’enregistrements par défaut. Pour les options disponibles, consultez [définition des Options de jeu d’enregistrements](#_core_setting_recordset_options).  
  
3.  Appelez l’objet [ouvrir](../../mfc/reference/crecordset-class.md#open) fonction membre.  
  
 Dans le constructeur, passez un pointeur vers un `CDatabase` de l’objet ou passer **NULL** à utiliser une variable temporaire des objets de base de données que l’infrastructure construit et ouvre basé sur la chaîne de connexion retournée par la [GetDefaultConnect ](../../mfc/reference/crecordset-class.md#getdefaultconnect) fonction membre. Le `CDatabase` objet peut déjà être connecté à une source de données.  
  
 L’appel à **ouvrir** utilise SQL pour sélectionner des enregistrements de la source de données. Le premier enregistrement sélectionné (le cas échéant) est l’enregistrement actif. Les valeurs des champs de cet enregistrement sont stockées dans les membres de données de champ de l’objet recordset. Si des enregistrements ont été sélectionnés, à la fois le `IsBOF` et `IsEOF` fonctions membres retournent 0.  
  
 Dans votre [ouvrir](../../mfc/reference/crecordset-class.md#open) appel, vous pouvez :  
  
-   Spécifiez si le recordset est une feuille de réponse dynamique ou un instantané. Par défaut, les jeux d’enregistrements sont ouverts en tant qu’instantanés. Ou bien, vous pouvez spécifier un jeu d’enregistrements avant uniquement, ce qui permet le défilement vers l’avant uniquement, un enregistrement à la fois.  
  
     Par défaut, un jeu d’enregistrements utilise le type par défaut stocké dans le `CRecordset` membre de données **m_nDefaultType**. Assistants écrivent du code pour initialiser **m_nDefaultType** pour le type de jeu d’enregistrements que vous choisissez dans l’Assistant. Au lieu d’accepter cette valeur par défaut, vous pouvez remplacer un autre type de jeu d’enregistrements.  
  
-   Spécifiez une chaîne pour remplacer la valeur par défaut SQL **sélectionnez** instruction le recordset construit.  
  
-   Spécifiez si le jeu d’enregistrements est en lecture seule ou en mode append-only. Autorise les jeux d’enregistrements complète de la mise à jour par défaut, mais vous pouvez limiter que pour l’ajout de nouveaux enregistrements uniquement ou vous pouvez ne pas autoriser les mises à jour.  
  
 L’exemple suivant montre comment ouvrir un objet instantané en lecture seule de la classe `CStudentSet`, une classe spécifique à l’application :  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 Après avoir appelé **ouvrir**, utilisez les membres de données et des fonctions membres de l’objet pour travailler avec les enregistrements. Dans certains cas, vous souhaiterez actualiser ou actualiser le jeu d’enregistrements pour inclure les modifications qui se sont produites sur la source de données. Pour plus d’informations, consultez [Recordset : actualisant un Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).  
  
> [!TIP]
>  La chaîne de connexion que vous utilisez pendant le développement ne peut pas être la même chaîne de connexion nécessitant les utilisateurs finaux. Pour des informations sur la généralisation de votre application à ce sujet, consultez [Source de données : gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).  
  
##  <a name="_core_setting_recordset_options"></a>Définition des Options de jeu d’enregistrements  
 Après avoir construit l’objet recordset, mais avant d’appeler **ouvrir** pour sélectionner des enregistrements, vous souhaiterez peut-être définir des options pour contrôler le comportement du recordset. Pour tous les jeux d’enregistrements, vous pouvez :  
  
-   Spécifiez un [filtre](../../data/odbc/recordset-filtering-records-odbc.md) pour contraindre la sélection des enregistrements.  
  
-   Spécifiez un [tri](../../data/odbc/recordset-sorting-records-odbc.md) afin que les enregistrements.  
  
-   Spécifiez [paramètres](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) afin de pouvoir sélectionner des enregistrements à l’aide des informations obtenues ou calculées au moment de l’exécution.  
  
 Vous pouvez également définir l’option suivante si les conditions sont remplies :  
  
-   Si le jeu d’enregistrements est modifiable et prend en charge les options de verrouillage, spécifiez la [verrouillage](../../data/odbc/recordset-locking-records-odbc.md) méthode utilisée pour les mises à jour.  
  
> [!NOTE]
>  Pour modifier la sélection des enregistrements, vous devez définir ces options avant d’appeler le **ouvrir** fonction membre.  
  
##  <a name="_core_closing_a_recordset"></a>Fermeture d’un Recordset  
 Lorsque vous avez terminé avec votre jeu d’enregistrements, vous devez la supprimer et désallouer sa mémoire.  
  
#### <a name="to-close-a-recordset"></a>Pour fermer un jeu d’enregistrements  
  
1.  Appeler son [fermer](../../mfc/reference/crecordset-class.md#close) fonction membre.  
  
2.  Détruire l’objet recordset.  
  
     Si vous l’avez déclarée sur le frame de pile d’une fonction, l’objet est détruit automatiquement lorsque l’objet est hors de portée. Sinon, utilisez le **supprimer** opérateur.  
  
 **Fermer** libère le jeu d’enregistrements **HSTMT** gérer. Elle ne supprime pas l’objet C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)   
 [Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)