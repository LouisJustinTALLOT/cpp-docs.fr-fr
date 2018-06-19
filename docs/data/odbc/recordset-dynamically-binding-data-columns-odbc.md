---
title: 'Recordset : Liaison dynamique de colonnes de données (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9fe71707de20ba02228039e5693cab9c9401d560
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093384"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Recordset : liaison dynamique de colonnes de données (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Les recordsets gèrent la liaison des colonnes de table que vous spécifiez au moment du design, mais il existe des cas lorsque vous souhaiterez peut-être lier les colonnes qui ont été inconnus au moment du design. Cette rubrique explique :  
  
-   [Lorsque vous souhaiterez lier dynamiquement des colonnes à un jeu d’enregistrements](#_core_when_you_might_bind_columns_dynamically).  
  
-   [Comment lier des colonnes dynamiquement au moment de l’exécution](#_core_how_to_bind_columns_dynamically).  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Les techniques décrites généralement ne sont pas recommandées si vous utilisez l’extraction de lignes en bloc. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a> Lorsque vous pouvez lier des colonnes dynamiquement  
 Au moment du design, l’Assistant Application MFC ou [Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (à partir de **ajouter une classe**) crée des classes de jeu d’enregistrements basés sur les tables et colonnes connues sur votre source de données. Bases de données peuvent varier lorsque vous concevez et celui où votre application utilise les tables et les colonnes en cours d’exécution. Vous ou un autre utilisateur peut ajouter ou supprimer une table ou ajouter ou supprimer des colonnes d’une table qui dépend de l’ensemble d’enregistrements de votre application. Cela est probablement pas un critère important pour toutes les applications d’accès aux données, mais si elle est le cas, comment pouvez-vous faire face à des modifications dans le schéma de base de données, autre que par une nouvelle conception et en recompilant ? L’objectif de cette rubrique est pour répondre à cette question.  
  
 Cette rubrique décrit le cas le plus courant dans lequel vous pouvez lier des colonnes dynamiquement : après avoir commencé avec un jeu d’enregistrements basé sur un schéma de base de données connue, vous souhaitez gérer des colonnes supplémentaires au moment de l’exécution. La rubrique présume que les colonnes supplémentaires sont mappés aux `CString` champ les membres de données, la plupart des cas, bien que des suggestions sont fournies pour vous aider à gérer d’autres types de données.  
  
 Avec une petite quantité de code supplémentaire, vous pouvez :  
  
-   [Déterminer les colonnes disponibles au moment de l’exécution](#_core_how_to_bind_columns_dynamically).  
  
-   [Lier dynamiquement des colonnes supplémentaires à votre jeu d’enregistrements en cours d’exécution](#_core_adding_the_columns).  
  
 Le jeu d’enregistrements contient toujours les membres de données pour les colonnes que vous connaissiez au moment du design. Il contient une petite quantité de code supplémentaires qui déterminent dynamiquement si de nouvelles colonnes ont été ajoutées à la table cible et, dans ce cas, lie ces nouvelles colonnes au stockage alloué dynamiquement (plutôt qu’aux membres de données de jeu d’enregistrements).  
  
 Cette rubrique ne couvre pas les autres cas de liaison dynamique, tels que des tables ou colonnes supprimées. Dans ces cas, vous devez utiliser les appels d’API ODBC directement. Pour plus d’informations, consultez le SDK ODBC *de référence du programmeur* sur le CD-ROM MSDN Library.  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a> Comment lier des colonnes dynamiquement  
 Pour lier des colonnes dynamiquement, vous devez connaître (ou être en mesure de déterminer) les noms des colonnes supplémentaires. Vous devez également allouer le stockage pour les membres de données de champ supplémentaires, spécifier leurs noms et leurs types et spécifiez le nombre de colonnes que vous ajoutez.  
  
 La discussion suivante mentionne les deux jeux d’enregistrements différents. Le premier est le recordset principal qui sélectionne les enregistrements de la table cible. Le deuxième est un jeu d’enregistrements de la colonne spéciale utilisée pour obtenir des informations sur les colonnes de la table cible.  
  
###  <a name="_core_the_general_process"></a> Processus général  
 Niveau le plus général, procédez comme suit :  
  
1.  Construisez l’objet recordset principal.  
  
     Si vous le souhaitez, passer un pointeur vers open `CDatabase` de l’objet ou être en mesure de fournir des informations de connexion à l’ensemble d’enregistrements de la colonne d’une autre manière.  
  
2.  Étapes pour ajouter des colonnes dynamiquement.  
  
     Consultez la procédure décrite dans l’ajout des colonnes ci-dessous.  
  
3.  Ouvrez le recordset principal.  
  
     Le jeu d’enregistrements sélectionne les enregistrements et utilise des record field exchange (RFX) pour lier les colonnes statiques (celles qui sont mappées aux membres de données de champ de recordset) et les colonnes dynamiques (mappées à l’espace de stockage supplémentaire que vous allouez).  
  
###  <a name="_core_adding_the_columns"></a> L’ajout des colonnes  
 Liaison dynamique ajouté des colonnes au moment de l’exécution nécessite les étapes suivantes :  
  
1.  Au moment de l’exécution, déterminer les colonnes qui figurent dans la table cible. Extraire une liste des colonnes qui ont été ajoutés à la table, car la classe de recordset a été conçue à partir de ces informations.  
  
     Une bonne approche est d’utiliser une classe de recordset de colonnes conçue pour interroger la source de données pour les informations de colonne pour la table cible (par exemple, la colonne nom et type de données).  
  
2.  Fournir un stockage pour les nouveaux membres de données de champ. Étant donné que la classe de recordset principal n’a pas de membres de données de champ pour les colonnes inconnues, vous devez fournir un emplacement pour stocker les noms, les valeurs de résultat et éventuellement les informations de type de données (si les colonnes sont de différents types de données).  
  
     Une approche consiste à générer une ou plusieurs listes dynamiques, une pour les nouveaux noms de colonnes, un autre pour leurs valeurs de résultat et une troisième pour les types de données (si nécessaire). Ces listes, notamment la liste de valeurs, fournissent les informations et le stockage nécessaire pour la liaison. La figure suivante illustre la création de ces listes.  
     ![Création des listes de colonnes pour une liaison dynamique](../../data/odbc/media/vc37w61.gif "vc37w61")  
Création des listes de colonnes pour la liaison dynamique  
  
3.  Ajouter un appel de fonction RFX dans votre recordset principal `DoFieldExchange` de fonction pour chaque colonne ajoutée. Ces appels RFX effectuent le travail de l’extraction d’un enregistrement, y compris les colonnes supplémentaires et liaison des colonnes aux données membres de jeu d’enregistrements ou à votre espace de stockage réservé dynamiquement pour eux.  
  
     Une approche consiste à ajouter une boucle à votre recordset principal `DoFieldExchange` fonction qui effectue une itération sur la liste des nouvelles colonnes et appelle la fonction RFX appropriée pour chaque colonne dans la liste. À chaque appel RFX, passez un nom de colonne à partir de la liste des colonnes nom et un emplacement de stockage dans le membre correspondant de la liste de valeurs de résultat.  
  
###  <a name="_core_lists_of_columns"></a> Listes de colonnes  
 Les quatre listes que vous avez besoin pour travailler avec sont affichés dans le tableau suivant.  
  
 **Colonnes de Table en cours (liste 1 dans l’illustration)** une liste des colonnes figurant dans la table sur la source de données. Cette liste peut correspondre à la liste des colonnes actuellement liées de votre recordset.  
  
 **Bound-Recordset-Columns (liste 2 dans l’illustration)**  
 Une liste des colonnes liées de votre recordset. Ces colonnes disposent déjà d’instructions RFX votre `DoFieldExchange` (fonction).  
  
 **Colonnes-To-Bind-Dynamically (liste 3 dans l’illustration)**  
 Une liste de colonnes dans la table mais pas dans le jeu d’enregistrements. Ce sont les colonnes que vous souhaitez lier de manière dynamique.  
  
 **Dynamic-Column-Values (liste 4 dans l’illustration)**  
 Une liste contenant un stockage pour les valeurs extraites des colonnes que vous liez dynamiquement. Éléments de cette liste correspondent à celles des colonnes-to-Bind-Dynamically, un à un.  
  
###  <a name="_core_building_your_lists"></a> Création des listes  
 Avec une stratégie générale à l’esprit, vous pouvez activer les détails. Les procédures décrites dans le reste de cette rubrique montrent comment créer les listes affichées dans [listes de colonnes](#_core_lists_of_columns). Les procédures vous aident à :  
  
-   [Déterminer les noms de colonnes pas dans le jeu d’enregistrements](#_core_determining_which_table_columns_are_not_in_your_recordset).  
  
-   [Fournir un stockage dynamique pour les colonnes qui vient d’être ajoutées à la table](#_core_providing_storage_for_the_new_columns).  
  
-   [Ajout dynamique de RFX appelle pour les nouvelles colonnes](#_core_adding_rfx_calls_to_bind_the_columns).  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Détermination des colonnes de Table ne figurant pas dans le jeu d’enregistrements  
 Créez une liste (Bound-Recordset-Columns, comme dans liste 2 dans l’illustration) qui contient une liste des colonnes déjà liées dans votre recordset principal. Puis générez une liste (colonnes-to-Bind-Dynamically, dérivée de colonnes de Table en cours et liés aux colonnes de recordsets) qui contient les noms de colonnes qui sont dans la table sur la source de données, mais pas dans votre recordset principal.  
  
##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Pour déterminer les noms de colonnes pas dans le jeu d’enregistrements (colonnes-to-Bind-Dynamically)  
  
1.  Créez une liste (Bound-Recordset-Columns) des colonnes déjà liées dans votre recordset principal.  
  
     Une approche consiste à créer des colonnes de recordsets limite au moment du design. Vous pouvez examiner visuellement les appels de fonction RFX dans le jeu d’enregistrements `DoFieldExchange` fonction pour obtenir ces noms. Ensuite, configurez votre liste sous forme de tableau sont initialisé avec les noms.  
  
     Par exemple, l’illustration montre Bound-Recordset-Columns (liste 2) avec trois éléments. Il manque la colonne Phone illustrée dans Current-Table-Columns (liste 1) liés aux colonnes de recordsets.  
  
2.  Comparer les colonnes de Table en cours et liés aux colonnes de recordsets pour générer une liste (colonnes-to-Bind-Dynamically) des colonnes non déjà liées dans votre recordset principal.  
  
     Une approche consiste à effectuer une boucle sur la liste des colonnes de la table au moment de l’exécution (colonnes de la Table en cours) et la liste des colonnes déjà liées dans votre jeu d’enregistrements (Bound-Recordset-Columns) en parallèle. Dans les colonnes-to-Bind-Dynamically, placez les noms dans actuel à des colonnes de Table qui n’apparaissent pas dans les colonnes de jeu d’enregistrements de limite.  
  
     Par exemple, l’illustration montre les colonnes-to-Bind-Dynamically (liste 3) avec un seul élément : la colonne Phone trouvée dans Current-Table-Columns (liste 1), mais pas dans Bound-Recordset-Columns (liste 2).  
  
3.  Créez une liste de Dynamic-Column-Values (comme dans la liste 4 dans l’illustration) dans lequel stocker les valeurs de données correspondant à chaque nom de colonne stockée dans la liste des colonnes pour une liaison dynamique (colonnes-to-Bind-Dynamically).  
  
     Les éléments de cette liste de jouent le rôle de nouveau jeu d’enregistrements de données membres de champ. Ils sont les emplacements de stockage dans lequel les colonnes dynamiques sont liées. Pour obtenir une description des listes, consultez [listes de colonnes](#_core_lists_of_columns).  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a> Fournir le stockage pour les nouvelles colonnes  
 Ensuite, configurez les emplacements de stockage pour les colonnes à lier dynamiquement. L’idée est de fournir un élément de liste dans lequel stocker la valeur de chaque colonne. Ces emplacements de stockage en parallèle les variables membres du jeu d’enregistrements, qui stockent les colonnes liées normalement.  
  
##### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Pour fournir un stockage dynamique pour les nouvelles colonnes (Dynamic-Column-Values)  
  
1.  Build Dynamic-Column-Values, parallèles à colonnes-to-Bind-Dynamically, pour contenir la valeur des données dans chaque colonne.  
  
     Par exemple, l’illustration montre Dynamic-Column-Values (liste 4) avec un seul élément : un `CString` objet qui contient le numéro de téléphone de l’enregistrement actuel : « 555-1212 ».  
  
     Dans la plupart des cas, Dynamic-Column-Values possède des éléments de type `CString`. Si vous êtes confronté à des colonnes de types de données différents, vous devez une liste qui peut contenir des éléments d’une variété de types.  
  
 Le résultat des procédures précédentes est deux listes principales : colonnes-to-Bind-Dynamically contenant les noms des colonnes et Dynamic-Column-Values, qui contient les valeurs dans les colonnes de l’enregistrement actif.  
  
> [!TIP]
>  Si les nouvelles colonnes ne sont pas tous du même type de données, vous pourriez une liste parallèle supplémentaire contenant les éléments qui définissent une certaine manière du type de chaque élément correspondant dans la liste des colonnes. (Vous pouvez utiliser les valeurs **AFX_RFX_BOOL**, **AFX_RFX_BYTE**, et ainsi de suite, si vous souhaitez. Ces constantes sont définies dans AFXDB. H.) Choisissez un type de liste basé sur la façon dont vous représentez les types de données de colonne.  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Ajout d’appels RFX pour lier les colonnes  
 Enfin, faire en sorte que la liaison dynamique de se produire en plaçant les appels RFX pour les nouvelles colonnes de votre `DoFieldExchange` (fonction).  
  
##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Pour ajouter dynamiquement les appels RFX des nouvelles colonnes  
  
1.  Dans votre recordset principal `DoFieldExchange` membres de fonction, ajoutez le code qui effectue une itération sur la liste des nouvelles colonnes (colonnes-to-Bind-Dynamically). Dans chaque boucle, extrayez un nom de colonne à partir de colonnes-to-Bind-Dynamically et une valeur de résultat de la colonne de valeurs de colonnes dynamiques. Passez ces éléments à l’appel de fonction RFX approprié au type de données de la colonne. Pour obtenir une description des listes, consultez [listes de colonnes](#_core_lists_of_columns).  
  
 En règle générale, dans votre `RFX_Text` vous extrayez des appels de fonction `CString` objets dans les listes, comme dans les lignes suivantes du code, où les colonnes-to-Bind-Dynamically est une `CStringList` appelée `m_listName` et valeurs de colonne dynamique est un `CStringList` appelée `m_listValue`:  
  
```  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 Pour plus d’informations sur les fonctions RFX, consultez [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans les *Class Library Reference*.  
  
> [!TIP]
>  Si les nouvelles colonnes ont des types de données différents, utilisez une instruction switch dans la boucle d’appeler la fonction RFX appropriée pour chaque type.  
  
 Lorsque l’infrastructure appelle `DoFieldExchange` pendant la **ouvrir** processus pour lier les colonnes au jeu d’enregistrements, les appels RFX des colonnes statiques lient ces colonnes. Puis la boucle appelle à plusieurs reprises les fonctions RFX pour les colonnes dynamiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : utilisation d’éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)