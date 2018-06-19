---
title: 'TN053 : Les Classes de la base de données personnaliser les Routines DFX pour DAO | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dfx
dev_langs:
- C++
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47d1c9769055e0ab69f57f58b136b7844cb1f860
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386091"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053 : personnaliser les routines DFX pour les classes de base de données DAO
> [!NOTE]
>  Les Assistants et l’environnement Visual C++ ne prennent pas en charge les DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser [modèles OLE DB](../data/oledb/ole-db-templates.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour les nouveaux projets. Vous devez uniquement utiliser DAO dans la maintenance des applications existantes.  
  
 Cette note technique décrit le mécanisme DAO record field exchange (DFX). Pour aider à comprendre ce qui se passe dans les routines DFX, le `DFX_Text` fonction est expliquée en détail, par exemple. Comme source d’informations pour cette note technique supplémentaire, vous pouvez examiner le code pour les autres fonctions DFX individuelles. Vous aurez probablement pas besoin une routine personnalisée de DFX aussi souvent que vous ayez une routine personnalisée de RFX (utilisée avec les classes de base de données ODBC).  
  
 Cette note technique contient :  
  
-   Vue d’ensemble DFX  
  
- [Exemples](#_mfcnotes_tn053_examples) à l’aide de DAO Record Field Exchange et la liaison dynamique  
  
- [Fonctionne de DFX](#_mfcnotes_tn053_how_dfx_works)  
  
- [Ce que fait votre Routine DFX personnalisées](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
- [Détails de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **Vue d’ensemble DFX**  
  
 Le mécanisme d’échange champs d’enregistrements DAO (DFX) est utilisé pour simplifier la procédure de récupération et de mise à jour des données lorsque vous utilisez la `CDaoRecordset` classe. Le processus est simplifié à l’aide des membres de données de la `CDaoRecordset` classe. En dérivant de `CDaoRecordset`, vous pouvez ajouter des membres de données à la classe dérivée représentant chaque champ dans une table ou une requête. Ce mécanisme « liaison statique » est simple, mais il ne peut pas être la méthode d’extraction/mise à jour de données de choix pour toutes les applications. DFX récupère chaque champ lié à chaque fois que l’enregistrement actif est modifié. Si vous développez une application dépendant des performances qui ne requiert pas l’extraction de chaque champ lors de la devise est modifié, « liaison dynamique » via `CDaoRecordset::GetFieldValue` et `CDaoRecordset::SetFieldValue` peut être la méthode d’accès aux données de choix.  
  
> [!NOTE]
>  DFX et la liaison dynamique ne sont pas mutuellement exclusives pour une utilisation hybride de liaison statique et dynamique peut être utilisée.  
  
## <a name="_mfcnotes_tn053_examples"></a> Exemple 1 : D’utilisation de DAO Record Field Exchange uniquement  
  
 (suppose `CDaoRecordset` : classe dérivée `CMySet` déjà ouverte)  
  
```  
// Add a new record to the customers table  
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```  
  
 **Exemple 2 : D’utilisation de la liaison dynamique uniquement**  
  
 (part du principe à l’aide de `CDaoRecordset` (classe), `rs`, et il est déjà ouvert)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```  
  
 **Exemple 3 : Utilisation de DAO Record Field Exchange et liaison dynamique**  
  
 (suppose d’exploration de données employé avec `CDaoRecordset`-classe dérivée `emp`)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();

 
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
    emp.GetFieldValue(_T("photo"),
    varPhoto);

 
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName,
    varPhoto);
```  
  
## <a name="_mfcnotes_tn053_how_dfx_works"></a> Fonctionne de DFX  
  
 Le mécanisme DFX fonctionne de façon similaire pour le mécanisme de record field exchange (RFX) utilisé par les classes ODBC MFC. Principes de DFX et RFX sont identiques, mais il existe de nombreuses différences internes. La conception de fonctions DFX a pratiquement tout le code est partagé par les routines DFX individuels. Au niveau le plus élevé DFX niveau effectue quelques éléments.  
  
-   DFX construit le code SQL **sélectionnez** SQL et la clause **paramètres** clause si nécessaire.  
  
-   DFX construit la structure de liaison utilisée par DAO `GetRows` (fonction) (plus loin dans cette rubrique).  
  
-   DFX gère la mémoire tampon de données utilisé pour détecter les champs modifiés (si le mécanisme de double tampon est utilisé)  
  
-   DFX gère la **NULL** et **DIRTY** état tableaux et définit les valeurs mises à jour si nécessaire.  
  
 Au cœur de la DFX mécanisme est la `CDaoRecordset` classe dérivée `DoFieldExchange` (fonction). Cette fonction envoie des appels aux fonctions DFX individuelles d’un type de l’opération appropriée. Avant d’appeler `DoFieldExchange` les fonctions MFC internes définissent le type d’opération. La liste suivante montre les différents types d’opération et une brève description.  
  
|Opération|Description|  
|---------------|-----------------|  
|**AddToParameterList**|Génère la clause de paramètres|  
|**AddToSelectList**|Clause SELECT de builds|  
|**BindField**|Définit la structure de liaison|  
|**BindParam**|Définit les valeurs de paramètre|  
|**Correction**|Définit l’état de la valeur NULL|  
|**AllocCache**|Alloue un cache pour vérification incorrecte|  
|**StoreField**|Enregistre l’enregistrement actif à mettre en cache|  
|**LoadField**|Cache de restaurations aux valeurs de membre|  
|**FreeCache**|Libère le cache|  
|`SetFieldNull`|Jeux de champ sur NULL & d’état|  
|**MarkForAddNew**|Marque les champs modifiés si ce n’est pas NULL PSEUDO|  
|**MarkForEdit**|If incorrecte de marques champs ne correspondent pas au cache|  
|**SetDirtyField**|Jeux de champ valeurs marqués comme modifiés|  
  
 Dans la section suivante, chaque opération est expliquée plus en détail pour `DFX_Text`.  
  
 La fonctionnalité la plus importante à comprendre concernant le processus d’échange de champs d’enregistrements DAO est qu’il utilise le `GetRows` fonction de la `CDaoRecordset` objet. DAO `GetRows` fonction peut fonctionner de plusieurs façons. Cette note technique décrit brièvement `GetRows` car il est en dehors de l’étendue de cette note technique.  
  
 DAO `GetRows` peut fonctionner de plusieurs manières.  
  
-   Il peut récupérer en même temps plusieurs enregistrements et plusieurs champs de données. Ainsi, pour accélérer l’accès avec la complication du traitement d’une structure de données de grande taille et les décalages appropriés à chaque champ de données et pour chaque enregistrement de données de la structure. MFC ne tire pas parti de cet enregistrement plusieurs mécanisme de récupération.  
  
-   Une autre façon `GetRows` pouvez travail consiste à permettre aux développeurs de spécifier les adresses de liaison pour les données récupérées de chaque champ d’un enregistrement de données.  
  
-   DAO sera également « rappeler » dans l’appelant pour les colonnes de longueur variable afin de permettre à l’appelant allouer de la mémoire. Cette deuxième fonctionnalité présente l’avantage de réduire le nombre de copies de données ainsi que ce qui permet un stockage direct de données des membres d’une classe (le `CDaoRecordset` classe dérivée). Cet deuxième mécanisme est la méthode MFC utilise pour lier à des membres de données dans `CDaoRecordset` des classes dérivées.  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> Ce que fait votre Routine DFX personnalisées  
 Il est évident à partir de cette discussion de l’opération la plus importante implémentée dans n’importe quelle fonction DFX doit être la possibilité de configurer les structures de données requis pour appeler correctement `GetRows`. Il existe un nombre d’autres opérations une fonction DFX doit également prendre en charge, mais aucune comme importantes ou complexes comme préparation correctement pour le `GetRows` appeler.  
  
 L’utilisation de DFX est décrite dans la documentation en ligne. Essentiellement, deux conditions sont requises. Tout d’abord, les membres doivent être ajoutés à la `CDaoRecordset` classe pour chaque champ lié et le paramètre dérivée. Après cela `CDaoRecordset::DoFieldExchange` doit être substituée. Notez que le type de données du membre est important. Il doit faire correspondre les données à partir du champ dans la base de données ou au moins être convertible en ce type. Par exemple un champ numérique dans la base de données, comme un entier long, peut toujours être converti en texte et lié à un `CString` membre, mais un champ de texte dans une base de données n’est pas nécessairement peut-être être converties en une représentation numérique, comme un entier long et lié à un long integ er membre. DAO et le moteur de base de données Microsoft Jet sont responsables de la conversion (plutôt que MFC).  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> Détails de DFX_Text  
 Comme mentionné précédemment, la meilleure façon d’expliquer le fonctionne de DFX consiste à étudier un exemple de travail. À cet effet parcourt les mécanismes internes de `DFX_Text` fonctionne très bien pour fournir au moins une connaissance élémentaire de DFX.  
  
 **AddToParameterList**  
 Cette opération génère le code SQL **paramètres** clause («`Parameters <param name>, <param type> ... ;`») requis par Jet. Chaque paramètre est nommé et typé (comme spécifié dans l’appel RFX). Consultez la fonction **CDaoFieldExchange::AppendParamType** (fonction) pour afficher les noms des différents types. Dans le cas de `DFX_Text`, le type utilisé est `text`.  
  
 **AddToSelectList**  
 Génère le code SQL **sélectionnez** clause. Cela est assez simple comme le nom de colonne spécifié par l’appel DFX est simplement ajouté («`SELECT <column name>, ...`»).  
  
 **BindField**  
 Les plus complexes des opérations. Comme mentionné précédemment, il s’agit où la structure de liaison DAO utilisé par `GetRows` est configuré. Comme vous pouvez le voir à partir du code dans `DFX_Text` les types d’informations dans la structure incluent le type DAO utilisé (**DAO_CHAR** ou **DAO_WCHAR** dans le cas de `DFX_Text`). En outre, le type de liaison utilisée est également configuré. Dans une section antérieure `GetRows` a été décrit brièvement, mais elle était suffisant expliquer que le type de liaison utilisée par MFC est toujours adresse directe (**DAOBINDING_DIRECT**). En outre, pour la liaison de colonne de longueur variable (comme `DFX_Text`) liaison de rappel est utilisée pour que MFC peut contrôler l’allocation de mémoire et spécifiez une adresse de la longueur correcte. Cela signifie que MFC peut toujours déterminer DAO « where » pour placer les données, ce qui permet la liaison directement à des variables de membre. Le reste de la structure de liaison est rempli avec des éléments tels que l’adresse de la fonction de rappel d’allocation de mémoire et le type de liaison de colonne (liaison par nom de colonne).  
  
 **BindParam**  
 Il s’agit d’une opération simple qui appelle `SetParamValue` avec la valeur du paramètre spécifiée dans le membre de paramètre.  
  
 **Correction**  
 Renseigne le **NULL** état pour chaque champ.  
  
 `SetFieldNull`  
 Cette opération marque seulement l’état de chaque champ en tant que **NULL** et définit le membre de valeur de la variable **PSEUDO_NULL**.  
  
 **SetDirtyField**  
 Appels `SetFieldValue` pour chaque champ marqué comme modifié.  
  
 Toutes les opérations restantes traitent uniquement à l’aide du cache de données. Le cache de données est une mémoire tampon des données dans l’enregistrement actif est utilisé pour simplifier certaines choses de supplémentaire. Par exemple, les champs « modifiées » peuvent être détectées automatiquement. Comme décrit dans la documentation en ligne, qu'il peut être désactivé complètement ou au niveau du champ. L’implémentation de la mémoire tampon utilise une carte. Ce mappage est utilisé pour mettre en correspondance les copies alloués de manière dynamique des données avec l’adresse du champ « lié » (ou `CDaoRecordset` dérivée du membre de données).  
  
 **AllocCache**  
 Dynamiquement alloue de la valeur du champ mis en cache et l’ajoute à la carte.  
  
 **FreeCache**  
 Supprime la valeur du champ mis en cache et le supprime de la carte.  
  
 **StoreField**  
 Copie la valeur du champ dans le cache de données.  
  
 **LoadField**  
 Copie la valeur mise en cache dans le membre de champ.  
  
 **MarkForAddNew**  
 Vérifie si la valeur actuelle du champ est non -**NULL** et marque incorrectes si nécessaire.  
  
 **MarkForEdit**  
 Compare la valeur de champ actuelle avec un cache de données et les marque incorrectes si nécessaire.  
  
> [!TIP]
>  Le modèle de vos routines DFX personnalisées sur les routines DFX existants pour les types de données standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

