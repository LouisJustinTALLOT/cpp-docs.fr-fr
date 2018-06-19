---
title: 'Recordset : Utilisation d’éléments de données volumineux (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6845d2e3c1b1eac31486200a0f610037d4774626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091733"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Recordset : utilisation d'éléments de données volumineux (ODBC)
Cette rubrique s’applique aux classes ODBC MFC et les classes DAO MFC.  
  
> [!NOTE]
>  Si vous utilisez les classes DAO MFC, gérez vos éléments de données volumineux avec la classe [CByteArray](../../mfc/reference/cbytearray-class.md) au lieu de la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). Si vous utilisez les classes ODBC MFC avec l’extraction de lignes en bloc, utilisez `CLongBinary` plutôt que `CByteArray`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Supposons que votre base de données peut stocker de grands fragments de données, comme les bitmaps (photos des employés, cartes, les images de produits, les objets OLE et ainsi de suite). Ce type de données est souvent appelé un objet binaire volumineux (ou BLOB), car :  
  
-   Chaque valeur de champ est grande.  
  
-   Contrairement aux numéros et autres types de données simples, il a sans taille prévisible.  
  
-   Les données sont sans forme du point de vue de votre programme.  
  
 Cette rubrique explique quelles prise en charge fournissent les classes de base de données pour travailler avec ces objets.  
  
##  <a name="_core_managing_large_objects"></a> Gestion d’objets volumineux  
 Jeux d’enregistrements ont deux façons de résoudre la difficulté de gestion des objets binaires volumineux. Vous pouvez utiliser la classe [CByteArray](../../mfc/reference/cbytearray-class.md) ou vous pouvez utiliser la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). En règle générale, `CByteArray` est recommandée pour gérer des données binaires volumineuses.  
  
 `CByteArray` nécessite un traitement plus que `CLongBinary` mais n’est plus performante, comme décrit dans [CByteArray, classe](#_core_the_cbytearray_class). `CLongBinary` est décrit brièvement dans [classe CLongBinary](#_core_the_clongbinary_class).  
  
 Pour plus d’informations sur l’utilisation de `CByteArray` pour travailler avec des éléments de données volumineux, consultez [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_cbytearray_class"></a> Classe CByteArray  
 `CByteArray` est une des classes de collection MFC. A `CByteArray` objet stocke un tableau dynamique d’octets, le tableau peut augmenter si nécessaire. La classe fournit un accès rapide par index, comme avec les tableaux C++ intégrés. `CByteArray` objets pouvant être sérialisés et vidées pour établir un diagnostic. La classe fournit des fonctions membres pour l’obtention et définition d’octets spécifié, insertion et ajouter des octets et supprimer un octet ou tous les octets. Ces fonctions facilitent l’analyse des données binaires. Par exemple, si l’objet binaire est un objet OLE, vous devrez peut-être fonctionne par le biais des octets d’en-tête pour atteindre l’objet réel.  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a> Utilisation de CByteArray dans les Recordsets  
 Grâce à un membre de données de champ de votre jeu d’enregistrements du type `CByteArray`, vous fournissez une base fixe à partir de laquelle [RFX](../../data/odbc/record-field-exchange-rfx.md) peut gérer le transfert d’un tel objet entre votre jeu d’enregistrements et de la source de données et grâce à laquelle vous pouvez manipuler la données à l’intérieur de l’objet. RFX a besoin d’un site spécifique pour les données extraites, et il vous faut un moyen pour accéder aux données sous-jacentes.  
  
 Pour plus d’informations sur l’utilisation de `CByteArray` pour travailler avec des éléments de données volumineux, consultez [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_clongbinary_class"></a> CLongBinary (classe)  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md) objet est un interpréteur de commandes simple autour d’un `HGLOBAL` handle vers un bloc de stockage alloué sur le tas. Quand il lie une colonne de table contenant un objet binaire volumineux, RFX alloue la `HGLOBAL` gérer lorsqu’il a besoin de transférer les données vers le recordset et stocke le descripteur dans le `CLongBinary` champ de l’objet recordset.  
  
 À son tour, vous utilisez la `HGLOBAL` gérer, `m_hData`, pour travailler avec les données lui-même, comme vous le feriez sur n’importe quel données. C’est là [CByteArray](../../mfc/reference/cbytearray-class.md) ajoute des fonctionnalités.  
  
> [!CAUTION]
>  Les objets CLongBinary ne peut pas être utilisés en tant que paramètres dans les appels de fonction. En outre, leur implémentation, qui appelle **:: SQLGetData**, nécessairement ralentit les performances de défilement d’un instantané de défilement. Cela peut être également vrai lorsque vous utilisez un **:: SQLGetData** appeler vous-même pour récupérer les colonnes de schéma dynamiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)