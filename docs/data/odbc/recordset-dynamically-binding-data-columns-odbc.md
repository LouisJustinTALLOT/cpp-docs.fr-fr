---
title: 'Recordset : Liaison dynamique des colonnes de données (ODBC) | Microsoft Docs'
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
ms.openlocfilehash: fe0be424b07fd9d13eec63c56172b2b0195b83d9
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338809"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Recordset : liaison dynamique de colonnes de données (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Jeux d’enregistrements de gérer les colonnes de table de liaison que vous spécifiez au moment du design, mais il existe des cas lorsque vous souhaiterez peut-être lier les colonnes qui étaient inconnus à vous au moment du design. Cette rubrique explique :  
  
-   [Lorsque vous pouvez souhaiter lier dynamiquement des colonnes à un jeu d’enregistrements](#_core_when_you_might_bind_columns_dynamically).  
  
-   [Comment lier des colonnes dynamiquement au moment de l’exécution](#_core_how_to_bind_columns_dynamically).  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Les techniques décrites généralement ne sont pas recommandées si vous utilisez l’extraction de lignes en bloc. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a> Quand vous pourriez lier des colonnes dynamiquement  
 Au moment du design, l’Assistant Application MFC ou [Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (à partir de **ajouter une classe**) crée des classes de jeu d’enregistrements basées sur les tables et colonnes connues sur votre source de données. Bases de données peuvent varier lorsque vous concevez et celui où votre application utilise les tables et les colonnes en cours d’exécution. Vous ou un autre utilisateur peut ajouter ou supprimer une table ou ajouter ou supprimer des colonnes d’une table de jeu d’enregistrements de votre application s’appuie sur. Cela est probablement pas un critère important pour toutes les applications d’accès aux données, mais si elle est le cas, comment pouvez-vous faire face à des modifications dans le schéma de base de données, autrement qu’en reconcevoir et une recompilation ? L’objectif de cette rubrique consiste à répondre à cette question.  
  
 Cette rubrique décrit le cas le plus courant dans lequel vous pourriez lier des colonnes dynamiquement : après avoir commencé avec un jeu d’enregistrements basé sur un schéma de base de données connue, vous souhaitez gérer des colonnes supplémentaires au moment de l’exécution. La rubrique présume que les colonnes supplémentaires sont mappés aux `CString` champ des membres de données, la plupart des cas, bien que les suggestions sont fournies pour vous aider à gérer d’autres types de données.  
  
 Avec une petite quantité de code supplémentaire, vous pouvez :  
  
-   [Déterminer quelles sont les colonnes sont disponibles au moment de l’exécution](#_core_how_to_bind_columns_dynamically).  
  
-   [Lier dynamiquement des colonnes supplémentaires à votre jeu d’enregistrements en cours d’exécution](#_core_adding_the_columns).  
  
 Votre jeu d’enregistrements contient toujours les membres de données pour les colonnes que vous connaissiez au moment du design. Il contient une petite quantité de code supplémentaire qui détermine dynamiquement si de nouvelles colonnes ont été ajoutées à la table cible et, dans ce cas, lie ces nouvelles colonnes au stockage alloué dynamiquement (plutôt qu’aux membres de données de jeu d’enregistrements).  
  
 Cette rubrique ne couvre pas les autres cas de liaison dynamique, tels que des tables ou colonnes supprimées. Dans ces cas, vous devez utiliser des appels d’API ODBC plus directement. Pour plus d’informations, consultez l’article ODBC SDK *de référence du programmeur* sur le CD MSDN Library.  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a> Comment lier des colonnes dynamiquement  
 Pour lier des colonnes dynamiquement, vous devez savoir (ou être en mesure de déterminer) les noms des colonnes supplémentaires. Vous devez également allouer le stockage pour les membres de données de champ supplémentaires, spécifier leurs noms et leurs types et spécifiez le nombre de colonnes que vous ajoutez.  
  
 La discussion suivante mentionne deux jeux d’enregistrements différents. Le premier est le recordset principal qui sélectionne les enregistrements de la table cible. Le second est un jeu d’enregistrements de colonne spéciale utilisée pour obtenir des informations sur les colonnes de la table cible.  
  
###  <a name="_core_the_general_process"></a> Processus général  
 Niveau le plus général, procédez comme suit :  
  
1.  Construire l’objet recordset principal.  
  
     Si vous le souhaitez, passer un pointeur vers une ouverture `CDatabase` de l’objet ou être en mesure de fournir des informations de connexion à l’ensemble d’enregistrements de la colonne d’une autre manière.  
  
2.  Prendre des mesures pour ajouter dynamiquement des colonnes.  
  
     Consultez la procédure décrite dans l’ajout des colonnes ci-dessous.  
  
3.  Ouvrez le recordset principal.  
  
     Le jeu d’enregistrements sélectionne les enregistrements et utilise des record field exchange (RFX) pour lier les colonnes statiques (celles qui sont mappées aux membres de données de champ de recordset) et les colonnes dynamiques (mappées à l’espace de stockage supplémentaire que vous allouez).  
  
###  <a name="_core_adding_the_columns"></a> Ajout des colonnes  
 Liaison dynamique ajouté des colonnes au moment de l’exécution nécessite les étapes suivantes :  
  
1.  Au moment de l’exécution, déterminer quelles colonnes figurent dans la table cible. Extraire une liste des colonnes qui ont été ajoutés à la table dans la mesure où votre classe de jeu d’enregistrements a été conçue à partir de ces informations.  
  
     Une bonne approche consiste à utiliser une classe de jeu d’enregistrements de colonnes conçue pour interroger la source de données pour les informations de colonne pour la table cible (par exemple, la colonne nom et type de données).  
  
2.  Fournir un stockage pour les nouveaux membres de données de champ. Étant donné que votre classe de recordset principal n’a pas de membres de données de champ pour les colonnes inconnues, vous devez fournir un emplacement pour stocker les noms, les valeurs de résultat et éventuellement les informations de type de données (si les colonnes sont les différents types de données).  
  
     Une approche consiste à créer une ou plusieurs listes dynamiques, un pour les nouveaux noms de colonnes, un autre pour leurs valeurs de résultat et une troisième pour leurs types de données (si nécessaire). Ces listes, en particulier la liste de valeurs, fournissent les informations et le stockage nécessaire pour la liaison. La figure suivante illustre la création de ces listes.  
     ![Création des listes de colonnes pour une liaison dynamique](../../data/odbc/media/vc37w61.gif "vc37w61")  
Création des listes de colonnes pour la liaison dynamiquement  
  
3.  Ajoutez un appel de fonction RFX dans votre recordset principal `DoFieldExchange` fonction pour chaque colonne ajoutée. Ces appels RFX effectuent le travail d’extraction d’un enregistrement, y compris les colonnes supplémentaires et liaison des colonnes aux membres de données de jeu d’enregistrements ou dans votre stockage dynamiquement fourni pour eux.  
  
     Une approche consiste à ajouter une boucle à votre recordset principal `DoFieldExchange` fonction qui effectue une itération sur la liste des nouvelles colonnes, appelle la fonction RFX appropriée pour chaque colonne dans la liste. À chaque appel RFX, passez un nom de colonne à partir de la liste des colonnes nom et un emplacement de stockage dans le membre correspondant de la liste de valeurs de résultat.  
  
###  <a name="_core_lists_of_columns"></a> Listes de colonnes  
 Les quatre listes que vous avez besoin pour travailler avec figurent dans le tableau suivant.  
  
 **Colonnes de Table en cours (liste 1 dans l’illustration)** une liste des colonnes figurant dans la table sur la source de données. Cette liste peut correspondre à la liste des colonnes actuellement liées du recordset.  
  
 **Colonnes de jeu d’enregistrements liées aux (liste 2 dans l’illustration)**  
 Liste des colonnes liées dans votre jeu d’enregistrements. Ces colonnes disposent déjà d’instructions RFX votre `DoFieldExchange` (fonction).  
  
 **Colonnes-To-Bind-Dynamically (liste 3 dans l’illustration)**  
 Une liste de colonnes dans la table mais pas dans le jeu d’enregistrements. Ce sont les colonnes que vous souhaitez lier dynamiquement.  
  
 **Valeurs de colonne dynamique (liste 4 dans l’illustration)**  
 Une liste contenant un stockage pour les valeurs extraites des colonnes que vous liez dynamiquement. Éléments de cette liste correspondent à celles des colonnes-to-Bind-Dynamically, un à un.  
  
###  <a name="_core_building_your_lists"></a> Création des listes  
 Avec une stratégie générale à l’esprit, vous pouvez activer pour les détails. Les procédures décrites dans le reste de cette rubrique vous montrent comment créer les listes affichées dans [listes de colonnes](#_core_lists_of_columns). Les procédures vous aident à :  
  
-   [Détermination des noms de colonnes pas dans votre jeu d’enregistrements](#_core_determining_which_table_columns_are_not_in_your_recordset).  
  
-   [En fournissant le stockage dynamique pour les colonnes qui vient d’être ajoutées à la table](#_core_providing_storage_for_the_new_columns).  
  
-   [Ajout dynamique de RFX appelle pour les nouvelles colonnes](#_core_adding_rfx_calls_to_bind_the_columns).  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Détermination des colonnes de Table ne figurant pas dans votre jeu d’enregistrements  
 Créez une liste (Bound-Recordset-Columns, comme dans 2 liste dans l’illustration) qui contient une liste des colonnes déjà liées dans votre recordset principal. Puis générez une liste (colonnes-to-Bind-Dynamically, dérivé des colonnes de Table actuelle et liés aux colonnes de recordsets) qui contient les noms de colonnes qui figurent dans la table sur la source de données, mais pas dans votre recordset principal.  
  
##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Pour déterminer les noms de colonnes pas dans le jeu d’enregistrements (colonnes-to-Bind-Dynamically)  
  
1.  Créez une liste (Bound-Recordset-Columns) des colonnes déjà liées dans votre recordset principal.  
  
     Une approche consiste à créer des colonnes de jeu d’enregistrements de limite au moment du design. Vous pouvez examiner visuellement les appels de fonction RFX dans le jeu d’enregistrements `DoFieldExchange` fonction pour obtenir ces noms. Ensuite, configurez votre liste sous forme de tableau initialisé avec les noms.  
  
     Par exemple, l’illustration montre les colonnes de jeu d’enregistrements liées aux (liste 2) avec trois éléments. Il manque la colonne Phone illustrée dans Current-Table-Columns (liste 1) liés aux colonnes de recordsets.  
  
2.  Comparer des colonnes de Table actuelle et liés aux colonnes de recordsets pour générer une liste (colonnes-to-Bind-Dynamically) des colonnes n’est pas encore lié dans votre recordset principal.  
  
     Une approche consiste à effectuer une boucle sur la liste des colonnes de la table au moment de l’exécution (colonnes de la Table en cours) et la liste des colonnes déjà liées dans votre jeu d’enregistrements (colonnes de jeu d’enregistrements liées aux) en parallèle. Dans les colonnes-to-Bind-Dynamically, placez les noms dans actuel-des colonnes de Table qui n’apparaissent pas dans les colonnes de jeu d’enregistrements de limite.  
  
     Par exemple, l’illustration montre les colonnes-to-Bind-Dynamically (liste 3) avec un seul élément : la colonne Phone trouvée dans Current-Table-Columns (liste 1), mais pas dans les colonnes de jeu d’enregistrements liées aux (liste 2).  
  
3.  Créez une liste de colonne-Dynamic-Values (comme dans la liste 4 dans l’illustration) dans lequel stocker les valeurs de données correspondant à chaque nom de colonne stockée dans la liste des colonnes pour une liaison dynamique (colonnes-to-Bind-Dynamically).  
  
     Les éléments de cette liste jouent le rôle de nouveau jeu d’enregistrements de données membres de champ. Ils sont les emplacements de stockage dans lequel les colonnes dynamiques sont liées. Pour obtenir une description des listes, consultez [listes de colonnes](#_core_lists_of_columns).  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a> Fournir le stockage pour les nouvelles colonnes  
 Ensuite, configurez les emplacements de stockage pour les colonnes à lier dynamiquement. L’idée est de fournir un élément de liste dans lequel stocker la valeur de chaque colonne. Ces emplacements de stockage en parallèle les variables de membres de jeu d’enregistrements, qui stockent les colonnes liées normalement.  
  
##### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Pour fournir le stockage dynamique pour les nouvelles colonnes (valeurs de colonne dynamique)  
  
1.  Build Dynamic-Column-Values, parallèles à colonnes-to-Bind-Dynamically, pour contenir la valeur des données dans chaque colonne.  
  
     Par exemple, l’illustration montre Dynamic-Column-Values (liste 4) avec un seul élément : un `CString` objet contenant le numéro de téléphone de l’enregistrement actuel : « 555-1212 ».  
  
     Dans le cas le plus courant, valeurs de colonne dynamique contient des éléments de type `CString`. Si vous êtes confronté à des colonnes de types de données différents, vous avez besoin d’une liste qui peut contenir des éléments d’une variété de types.  
  
 Le résultat des procédures précédentes est deux listes principales : colonnes-to-Bind-Dynamically contenant les noms des colonnes et Dynamic-Column-Values, contenant les valeurs dans les colonnes de l’enregistrement actuel.  
  
> [!TIP]
>  Si les nouvelles colonnes ne sont pas tous du même type de données, vous souhaiterez peut-être une liste parallèle supplémentaire contenant les éléments qui définissent d’une certaine manière le type de chaque élément correspondant dans la liste des colonnes. (Vous pouvez utiliser les valeurs AFX_RFX_BOOL, AFX_RFX_BYTE, et ainsi de suite, si vous le souhaitez. Ces constantes sont définies dans AFXDB. H.) Choisissez un type de liste basé sur la façon dont vous représenter les types de données de colonne.  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Ajout d’appels RFX pour lier les colonnes  
 Enfin, faire en sorte que la liaison dynamique se produise en plaçant les appels RFX pour les nouvelles colonnes dans votre `DoFieldExchange` (fonction).  
  
##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Pour ajouter dynamiquement les appels RFX pour les nouvelles colonnes  
  
1.  Dans votre recordset principal `DoFieldExchange` membre de fonction, ajoutez le code qui effectue une itération sur la liste des nouvelles colonnes (colonnes-to-Bind-Dynamically). Dans chaque boucle, extraire un nom de colonne à partir de colonnes-to-Bind-Dynamically et une valeur de résultat pour la colonne de valeurs de colonnes dynamiques. Passez ces éléments à un appel de fonction RFX approprié au type de données de la colonne. Pour obtenir une description des listes, consultez [listes de colonnes](#_core_lists_of_columns).  
  
 Dans le cas courant, dans votre `RFX_Text` vous extrayez des appels de fonction `CString` objets dans les listes, comme dans les lignes suivantes de code, où les colonnes-to-Bind-Dynamically est un `CStringList` appelée `m_listName` et valeurs de colonne dynamique est un `CStringList` appelée `m_listValue`:  
  
```cpp  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 Pour plus d’informations sur les fonctions RFX, consultez [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans le *Class Library Reference*.  
  
> [!TIP]
>  Si les nouvelles colonnes sont les différents types de données, utilisez une instruction switch dans la boucle d’appeler la fonction RFX appropriée pour chaque type.  
  
 Lorsque l’infrastructure appelle `DoFieldExchange` pendant la `Open` processus pour lier les colonnes pour le jeu d’enregistrements, les appels RFX pour ces colonnes, liez les colonnes statiques. Puis votre boucle appelle à plusieurs reprises les fonctions RFX pour les colonnes dynamiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : utilisation d’éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)