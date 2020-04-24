---
title: Classe CDaoRecordset
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 6a1475d1b0bc083cfd180ea5a211e752c973e2f8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754682"
---
# <a name="cdaorecordset-class"></a>Classe CDaoRecordset

Représente un ensemble d'enregistrements sélectionnés à partir d'une source de données.

## <a name="syntax"></a>Syntaxe

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|Construit un objet `CDaoRecordset`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoRecordset::AddNew](#addnew)|Se prépare à l’ajout d’un nouvel album. [Mise à jour](#update) de l’appel pour compléter l’ajout.|
|[CDaoRecordset::CanAppend](#canappend)|Retourne nonzero si de nouveaux enregistrements peuvent être ajoutés à l’ensemble d’enregistrements via la fonction membre [AddNew.](#addnew)|
|[CDaoRecordset::CanBookmark](#canbookmark)|Retourne nonzero si le livre prend en charge les signets.|
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Annule toutes les mises à jour en attente en raison d’une opération [Edit](#edit) ou [AddNew.](#addnew)|
|[CDaoRecordset::CanRestart](#canrestart)|Retourne nonzero si [Requery](#requery) peut être appelé pour exécuter la requête du recordet à nouveau.|
|[CDaoRecordset::CanScroll](#canscroll)|Retourne nonzero si vous pouvez faire défiler les enregistrements.|
|[CDaoRecordset::CanTransact](#cantransact)|Retourne nonzero si la source de données prend en charge les transactions.|
|[CDaoRecordset::CanUpdate](#canupdate)|Retourne nonzero si le jeu d’enregistrement peut être mis à jour (vous pouvez ajouter, mettre à jour ou supprimer des enregistrements).|
|[CDaoRecordset::Fermer](#close)|Ferme le recordet.|
|[CDaoRecordset::Delete](#delete)|Supprime l’enregistrement actuel de l’enregistrement. Vous devez faire défiler explicitement vers un autre enregistrement après la suppression.|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|Appelé à échanger des données (dans les deux sens) entre les membres des données sur le terrain de l’enregistrement et l’enregistrement correspondant sur la source de données. Implémente l’échange de records DAO sur le terrain (DFX).|
|[CDaoRecordset::Edit](#edit)|Se prépare aux changements apportés au dossier actuel. Appelez `Update` pour terminer la modification.|
|[CDaoRecordset::FillCache](#fillcache)|Remplit tout ou partie d’un cache local pour un objet de numérot qui contient des données provenant d’une source de données ODBC.|
|[CDaoRecordset::Trouver](#find)|Localise la première, la prochaine, la précédente ou la dernière position d’une chaîne particulière dans un ensemble d’enregistrements de type dynaset qui répond aux critères spécifiés et qui enregistre l’enregistrement actuel.|
|[CDaoRecordset::FindFirst](#findfirst)|Localise le premier enregistrement dans un ensemble d’enregistrements de type dynaset ou instantané qui répond aux critères spécifiés et qui enregistre l’enregistrement actuel.|
|[CDaoRecordset::FindLast](#findlast)|Localise le dernier enregistrement dans un ensemble d’enregistrements de type dynaset ou instantané qui répond aux critères spécifiés et qui enregistre l’enregistrement actuel.|
|[CDaoRecordset::FindNext](#findnext)|Localise l’enregistrement suivant dans un enregistrement de type dynaset ou instantané qui satisfait les critères spécifiés et qui rend cet enregistrement de l’enregistrement actuel.|
|[CDaoRecordset::FindPrev](#findprev)|Localise l’enregistrement précédent dans un ensemble d’enregistrements de type dynaset ou instantané qui répond aux critères spécifiés et qui rend cet enregistrement de l’enregistrement actuel.|
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|Retourne le nombre record de l’enregistrement actuel d’un objet de recordet.|
|[CDaoRecordset::GetBookmark](#getbookmark)|Retourne une valeur qui représente le signet d’un enregistrement.|
|[CDaoRecordset::GetCacheSize](#getcachesize)|Retourne une valeur qui précise le nombre d’enregistrements dans un ensemble d’enregistrements de type dynaset contenant des données à mettre en cache localement à partir d’une source de données ODBC.|
|[CDaoRecordset::GetCacheStart](#getcachestart)|Retourne une valeur qui spécifie le signet du premier enregistrement dans le livre d’enregistrement à mettre en cache.|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Retourne `CString` un contenant le nom de l’index le plus `CDaoRecordset`récemment utilisé sur un indexé, de type table .|
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Retourne la date et l’heure de la création d’un objet sous-jacent à la `CDaoRecordset` table de base|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Renvoie la date et l’heure de la modification la `CDaoRecordset` plus récente apportée à la conception d’une table de base sous-jacente à un objet.|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Retourne le nom de la source de données par défaut.|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Appelé pour obtenir la chaîne SQL par défaut à exécuter.|
|[CDaoRecordset::GetEditMode](#geteditmode)|Retourne une valeur qui indique l’état d’édition de l’enregistrement actuel.|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Retourne une valeur qui représente le nombre de champs dans un jeu d’enregistrement.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Renvoie des types spécifiques d’informations sur les champs dans le dossier.|
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|Retourne la valeur d’un champ dans un jeu d’enregistrement.|
|[CDaoRecordset::GetIndexCount](#getindexcount)|Récupère le nombre d’index dans un tableau sous-jacent à un jeu d’enregistrement.|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Renvoie divers types d’informations sur un index.|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Utilisé pour déterminer l’enregistrement le plus récemment ajouté ou mis à jour.|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Retourne une valeur qui indique le type de verrouillage qui est en vigueur lors de l’édition.|
|[CDaoRecordset::GetName](#getname)|Retourne `CString` un contenant le nom de l’enregistrement.|
|[CDaoRecordset::GetParamValue](#getparamvalue)|Récupère la valeur actuelle du paramètre spécifié stocké dans l’objet DAOParameter sous-jacent.|
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|Retourne la position du dossier actuel en pourcentage du nombre total d’enregistrements.|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements accessibles dans un objet de recordet.|
|[CDaoRecordset::GetSQL](#getsql)|Obtient la chaîne SQL utilisé pour sélectionner les enregistrements pour le nombre d’enregistrements.|
|[CDaoRecordset::GetType](#gettype)|Appelé pour déterminer le type d’un ensemble d’enregistrements : type de table, type dynaset ou type instantané.|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Retourne `CString` une valeur contenante qui valide les données au fur et à mesure qu’elles sont entrées dans un champ.|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Récupère le texte qui s’affiche lorsqu’une règle de validation n’est pas satisfaite.|
|[CDaoRecordset::IsBOF](#isbof)|Retourne nonzero si le recordet a été positionné avant le premier enregistrement. Aucun enregistrement actif.|
|[CDaoRecordset::IsDeleted](#isdeleted)|Retourne nonzero si le recordet est positionné sur un enregistrement supprimé.|
|[CDaoRecordset::IsEOF](#iseof)|Retourne nonzero si le recordet a été positionné après le dernier enregistrement. Aucun enregistrement actif.|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Retourne nonzero si le champ spécifié dans l’enregistrement actuel a été modifié.|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Retourne nonzero si le champ spécifié dans le dossier actuel est Null (n’ayant aucune valeur).|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Retourne nonzero si le champ spécifié dans l’enregistrement actuel peut être réglé à Null (n’ayant aucune valeur).|
|[CDaoRecordset::IsOpen](#isopen)|Retourne nonzero si [Open](#open) a été appelé précédemment.|
|[CDaoRecordset::Déplacer](#move)|Positionne l’enregistrement à un nombre précis d’enregistrements de l’enregistrement actuel dans les deux sens.|
|[CDaoRecordset::MoveFirst](#movefirst)|Positionne le record actuel du premier enregistrement dans le dossier.|
|[CDaoRecordset::MoveLast](#movelast)|Positionne le record actuel du dernier enregistrement dans le dossier.|
|[CDaoRecordset::MoveNext](#movenext)|Positionne le record actuel sur le prochain enregistrement dans le record .|
|[CDaoRecordset::MovePrev](#moveprev)|Positionne le record actuel du précédent record dans le dossier.|
|[CDaoRecordset::Ouvert](#open)|Crée un nouvel ensemble d’enregistrements à partir d’une table, dynaset, ou instantané.|
|[CDaoRecordset::Requery](#requery)|Exécute la requête du recordet à nouveau pour rafraîchir les enregistrements sélectionnés.|
|[CDaoRecordset::Chercher](#seek)|Localise l’enregistrement dans un objet indexé de type tableau qui satisfait les critères spécifiés pour l’indice actuel et qui enregistre l’enregistrement actuel.|
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|Établit le nombre record de l’enregistrement actuel d’un objet de recordet.|
|[CDaoRecordset::SetBookmark](#setbookmark)|Positionne l’enregistrement sur un enregistrement contenant le signet spécifié.|
|[CDaoRecordset::SetCacheSize](#setcachesize)|Définit une valeur qui précise le nombre d’enregistrements dans un ensemble d’enregistrements de type dynaset contenant des données à mettre en cache localement à partir d’une source de données ODBC.|
|[CDaoRecordset::SetCacheStart](#setcachestart)|Définit une valeur qui spécifie le signet du premier enregistrement dans le livre d’enregistrement à mettre en cache.|
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|Appelé à établir un index sur un jeu de disques de type table.|
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|Marque le champ spécifié dans le dossier actuel tel que modifié.|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Définit la valeur du champ spécifié dans le dossier actuel à Null (n’ayant aucune valeur).|
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Définit la valeur d’un champ dans un jeu d’enregistrement.|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Définit la valeur d’un champ dans un ensemble d’enregistrements à Null. (n’ayant aucune valeur).|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Définit une valeur qui indique le type de verrouillage à mettre en œuvre lors de l’édition.|
|[CDaoRecordset::SetParamValue](#setparamvalue)|Définit la valeur actuelle du paramètre spécifié stocké dans l’objet DAOParameter sous-jacent|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Définit la valeur actuelle du paramètre spécifié à Null (n’ayant aucune valeur).|
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|Définit la position du dossier actuel à un endroit correspondant à un pourcentage du nombre total d’enregistrements dans un ensemble d’enregistrements.|
|[CDaoRecordset::Mise à jour](#update)|Termine une `AddNew` `Edit` ou une opération en économisant les données nouvelles ou modifiées sur la source de données.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Contient un drapeau indiquant si les champs sont automatiquement marqués comme modifiés.|
|[CDaoRecordset::m_nFields](#m_nfields)|Contient le nombre de membres des données sur le terrain dans la classe des enregistrements et le nombre de colonnes sélectionnées par le groupe d’enregistrement à partir de la source de données.|
|[CDaoRecordset::m_nParams](#m_nparams)|Contient le nombre de paramètres membres dans la classe de l’enregistrement — le nombre de paramètres passés avec la requête du recordet|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Un pointeur de l’interface DAO sous-jacente à l’objet de l’ensemble de disques.|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Base de données source pour cet ensemble de résultats. Contient un pointeur à un objet [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)|
|[CDaoRecordset::m_strFilter](#m_strfilter)|Contient une chaîne utilisée pour construire une déclaration SQL **WHERE.**|
|[CDaoRecordset::m_strSort](#m_strsort)|Contient une chaîne utilisée pour construire un SQL **ORDER BY** déclaration.|

## <a name="remarks"></a>Notes

Connus sous le `CDaoRecordset` nom de « records », les objets sont disponibles sous les trois formes suivantes :

- Les enregistrements de type table représentent une table de base que vous pouvez utiliser pour examiner, ajouter, modifier ou supprimer des enregistrements d’une seule table de base.

- Les enregistrements de type Dynaset sont le résultat d’une requête qui peut avoir des enregistrements à jour. Ces enregistrements sont un ensemble d’enregistrements que vous pouvez utiliser pour examiner, ajouter, modifier ou supprimer des enregistrements d’une table de base de données sous-jacente ou des tableaux. Les enregistrements de type Dynaset peuvent contenir des champs à partir d’une ou plusieurs tables d’une base de données.

- Les ensembles d’enregistrements de type instantané sont une copie statique d’un ensemble d’enregistrements que vous pouvez utiliser pour trouver des données ou générer des rapports. Ces enregistrements peuvent contenir des champs à partir d’une ou plusieurs tables d’une base de données, mais ne peuvent pas être mis à jour.

Chaque forme de jeu d’enregistrement représente un ensemble d’enregistrements fixés au moment de l’ouverture du jeu d’enregistrement. Lorsque vous faites défiler vers un enregistrement dans un jeu d’enregistrement de type table ou un jeu dynaset de type, il reflète les modifications apportées à l’enregistrement après l’ouverture du jeu d’enregistrement, soit par d’autres utilisateurs, soit par d’autres enregistrements de votre application. (Un jeu d’enregistrement de type instantané ne peut pas être mis à jour.) Vous pouvez `CDaoRecordset` utiliser directement ou tirer une `CDaoRecordset`classe de documents spécifique à l’application de . Ensuite, vous pouvez :

- Faites défiler les enregistrements.

- Définissez un index et recherchez rapidement des enregistrements à l’aide de [Seek](#seek) (enregistrements de type table uniquement).

- Trouvez des enregistrements basés sur une comparaison de\<chaînes : « < », « « », « >» ou « > » (enregistrements de type dynaset et de type instantané).

- Mettez à jour les enregistrements et spécifier un mode de verrouillage (à l’exception des enregistrements de type instantané).

- Filtrer le groupe d’enregistrement pour limiter les enregistrements qu’il sélectionne parmi ceux disponibles sur la source de données.

- Trier le recordet.

- Paramélisez le tableau d’enregistrement pour personnaliser sa sélection avec des informations non connues avant l’heure d’exécution.

La `CDaoRecordset` classe fournit une interface `CRecordset`similaire à celle de la classe . La principale différence `CDaoRecordset` est que la classe accède aux données via un objet d’accès aux données (DAO) basé sur OLE. La `CRecordset` classe accède au DBMS par l’intermédiaire de La connectivité de base de données ouverte (ODBC) et d’un pilote ODBC pour cela DBMS.

> [!NOTE]
> Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur la connectivité open Database (ODBC). Tous les noms de classe de base de données DAO ont le préfixe "CDao". Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO; les classes DAO offrent généralement des capacités supérieures parce qu’elles sont spécifiques au moteur de base de données Microsoft Jet.

Vous pouvez `CDaoRecordset` soit utiliser directement `CDaoRecordset`ou tirer une classe de . Pour utiliser une classe de disques dans les deux cas, ouvrez une base `CDaoDatabase` de données et construisez un objet de la taille d’enregistrement, en passant le constructeur d’un pointeur sur votre objet. Vous pouvez également `CDaoRecordset` construire un objet et `CDaoDatabase` laisser MFC créer un objet temporaire pour vous. Appelez ensuite la fonction de membre [Open](#open) du recordet, en précisant si l’objet est un ensemble de documents de type table, un jeu dynaset de type enregistrement, ou un jeu d’enregistrement de type instantané. L’appel `Open` sélectionne les données de la base de données et récupère le premier enregistrement.

Utilisez les fonctions des membres et les membres des données de l’objet pour faire défiler les enregistrements et les utiliser. Les opérations disponibles dépendent de la question de savoir si l’objet est un ensemble d’enregistrements de type table, un ensemble d’enregistrements de type dynaset ou un ensemble d’enregistrements de type instantané, et s’il est mis à jour ou lu uniquement — cela dépend de la capacité de la base de données ou de la source de données Open Database Connectivity (ODBC). Pour actualiser les enregistrements qui peuvent `Open` avoir été modifiés ou ajoutés depuis l’appel, appelez la fonction de membre [Requery](#requery) de l’objet. Appelez la fonction `Close` membre de l’objet et détruisez l’objet lorsque vous en avez terminé.

`CDaoRecordset`utilise L’échange de champs de disques DAO (DFX) pour soutenir la `CDaoRecordset` lecture `CDaoRecordset`et la mise à jour des champs d’enregistrement par l’intermédiaire de membres CMD de votre classe ou dérivés de votre catégorie de type-safe. Vous pouvez également implémenter la liaison dynamique des colonnes dans une base de données sans utiliser le mécanisme DFX à l’aide [de GetFieldValue](#getfieldvalue) et [SetFieldValue](#setfieldvalue).

Pour plus d’informations connexes, consultez le sujet "Objet Recordet" dans DAO Help.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a>CDaoRecordset::AddNew

Appelez cette fonction de membre pour ajouter un nouvel enregistrement à un jeu d’enregistrement de type table ou de type dynaset.

```
virtual void AddNew();
```

### <a name="remarks"></a>Notes

Les champs de l’enregistrement sont d’abord Nuls. (Dans la terminologie de la base de données, Null signifie « n’avoir aucune valeur » et n’est pas le même que NULL dans C.) Pour terminer l’opération, vous devez appeler la fonction membre [de mise à jour.](#update) `Update`enregistre vos modifications à la source de données.

> [!CAUTION]
> Si vous modifiez un enregistrement, puis `Update`faites défiler vers un autre enregistrement sans appeler, vos modifications sont perdues sans avertissement.

Si vous ajoutez un enregistrement à un jeu d’enregistrement de type dynaset en appelant [AddNew](#addnew), l’enregistrement `CDaoRecordset` est visible dans le jeu d’enregistrements et inclus dans le tableau sous-jacent où il devient visible à tous les nouveaux objets.

La position du nouvel enregistrement dépend du type d’enregistrement :

- Dans un jeu dynaset de type record, où le nouvel enregistrement est inséré n’est pas garanti. Ce comportement a changé avec Microsoft Jet 3.0 pour des raisons de performance et de concurrence. Si votre objectif est de faire le disque nouvellement ajouté le record actuel, obtenez le signet du dernier enregistrement modifié et passez à ce signet :

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- Dans un tableau de type enregistrement pour lequel un index a été spécifié, les enregistrements sont retournés à leur place dans l’ordre de tri. Si aucun indice n’a été spécifié, de nouveaux enregistrements sont retournés à la fin de l’enregistrement.

Le dossier qui était `AddNew` à jour avant votre utilisation reste à jour. Si vous souhaitez faire le nouvel enregistrement actuel et que le recordet prend en charge les signets, appelez [SetBookmark](#setbookmark) sur le signet identifié par l’établissement de propriété LastModified de l’objet DAO recordset sous-jacent. Cela est utile pour déterminer la valeur pour les champs de compteur (auto-incrément) dans un enregistrement supplémentaire. Pour plus d’informations, voir [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Si la base de données `AddNew` prend en charge les transactions, vous pouvez effectuer une partie de votre appel d’une transaction. Pour plus d’informations sur les transactions, voir classe [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Notez que vous devez appeler [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) avant d’appeler `AddNew`.

Il est illégal `AddNew` d’appeler à un recordet dont la fonction de membre [Open](#open) n’a pas été appelé. A `CDaoException` est lancé `AddNew` si vous appelez pour un enregistrement qui ne peut pas être joint. Vous pouvez déterminer si le recordet est mis à jour en appelant [CanAppend](#canappend).

Le cadre marque les données modifiées des membres des données sur le terrain pour s’assurer qu’ils seront écrits au dossier sur la source de données par le mécanisme d’échange de champs de disques DAO (DFX). Changer la valeur d’un champ définit généralement le champ sale automatiquement, de sorte que vous aurez rarement besoin d’appeler [SetFieldDirty](#setfielddirty) vous-même, mais vous voudrez peut-être parfois s’assurer que les colonnes seront explicitement mis à jour ou insérés quelle que soit la valeur dans le membre des données sur le terrain. Le mécanisme DFX utilise également **PSEUDO NULL**. Pour plus d’informations, voir [CDaoFieldExchange:m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si le mécanisme de double tampon n’est pas utilisé, alors changer la valeur du champ ne met pas automatiquement le champ comme sale. Dans ce cas, il sera nécessaire de mettre explicitement le champ sale. Le drapeau contenu dans [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) contrôle cette vérification automatique sur le terrain.

> [!NOTE]
> Si les enregistrements sont à double tampon (c’est-à-dire que la vérification automatique du terrain est activée), l’appel `CancelUpdate` rétablira les variables du membre aux valeurs qu’ils avaient auparavant `AddNew` ou `Edit` qu’on l’appelle.

Pour plus d’informations, consultez les thèmes "AddNew Method", "CancelUpdate Method", "LastModified Property", et "EditMode Property" dans DAO Help.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a>CDaoRecordset::CanAppend

Appelez cette fonction de membre pour déterminer si le recordet précédemment ouvert vous permet d’ajouter de nouveaux enregistrements en appelant la fonction membre [AddNew.](#addnew)

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet permet d’ajouter de nouveaux enregistrements; sinon 0. `CanAppend`reviendra 0 si vous avez ouvert le recordet comme lu uniquement.

### <a name="remarks"></a>Notes

Pour plus d’informations connexes, consultez le thème « Méthode d’annexe » dans DAO Help.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>CDaoRecordset::CanBookmark

Appelez cette fonction de membre pour déterminer si le jeu d’enregistrement précédemment ouvert vous permet de marquer individuellement les enregistrements à l’aide de signets.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le livre prend en charge les signets, sinon 0.

### <a name="remarks"></a>Notes

Si vous utilisez des enregistrements entièrement basés sur les tables de moteur de base de données Microsoft Jet, les signets peuvent être utilisés, sauf sur des enregistrements de type instantané marqués comme des enregistrements défilants avant-seulement. D’autres produits de base de données (sources externes de données ODBC) peuvent ne pas prendre en charge les signets.

Pour plus d’informations connexes, consultez le thème «Propriété bookmarkable» dans DAO Aide.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>CDaoRecordset::CancelUpdate

La `CancelUpdate` fonction membre annule toutes les mises à jour en attente en raison d’une opération [Edit](#edit) ou [AddNew.](#addnew)

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Notes

Par exemple, si une `Edit` `AddNew` application appelle la fonction `CancelUpdate` ou le membre `Edit` et `AddNew` n’a pas appelé [mise à jour,](#update)annule toute modification apportée après ou a été appelée.

> [!NOTE]
> Si les enregistrements sont à double tampon (c’est-à-dire que la vérification automatique du terrain est activée), l’appel `CancelUpdate` rétablira les variables du membre aux valeurs qu’ils avaient auparavant `AddNew` ou `Edit` qu’on l’appelle.

S’il `Edit` n’y a pas d’opération `AddNew` en attente, `CancelUpdate` le MFC fait une exception. Appelez la fonction membre [GetEditMode](#geteditmode) pour déterminer s’il y a une opération en cours qui peut être annulée.

Pour plus d’informations connexes, consultez le sujet "CancelUpdate Method" dans DAO Help.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a>CDaoRecordset::CanRestart

Appelez cette fonction de membre pour déterminer si le recordet permet de `Requery` redémarrer sa requête (pour actualiser ses dossiers) en appelant la fonction de membre.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Valeur de retour

Nonzero `Requery` si peut être appelé pour exécuter la requête du recordet à nouveau, sinon 0.

### <a name="remarks"></a>Notes

Les enregistrements de type `Requery`table ne prennent pas en charge .

Si `Requery` elle n’est pas prise en charge, appelez [Close](#close) puis [Ouvrez](#open) pour actualiser les données. Vous pouvez `Requery` appeler pour mettre à jour la requête sous-jacente du paramètre d’un objet de l’enregistrement après que les valeurs de paramètres ont été modifiées.

Pour obtenir des informations connexes, consultez le thème « Propriété redémarrée » dans DAO Help.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a>CDaoRecordset::CanScroll

Appelez cette fonction de membre pour déterminer si l’enregistrement permet de faire défiler.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si vous pouvez faire défiler les enregistrements, sinon 0.

### <a name="remarks"></a>Notes

Si vous [Open](#open) appelez `dbForwardOnly`Open avec , le recordet ne peut faire défiler vers l’avant.

Pour plus d’informations connexes, voir le sujet "Positionner le pointeur d’enregistrement actuel avec DAO" dans DAO Help.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a>CDaoRecordset::CanTransact

Appelez cette fonction de membre pour déterminer si l’enregistrement permet des transactions.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la source de données sous-jacente prend en charge les transactions, sinon 0.

### <a name="remarks"></a>Notes

Pour obtenir des informations connexes, consultez le thème « Transactions Property » dans DAO Help.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a>CDaoRecordset::CanUpdate

Appelez cette fonction de membre pour déterminer si l’enregistrement peut être mis à jour.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le jeu d’enregistrement peut être mis à jour (ajouter, mettre à jour et supprimer des enregistrements), sinon 0.

### <a name="remarks"></a>Notes

Un jeu d’enregistrement peut être lu uniquement si la source `dbReadOnly` de données sous-jacente est lue uniquement ou si vous avez spécifié pour *les nOptions* lorsque vous avez appelé [Open](#open) for the recordset.

Pour plus d’informations connexes, consultez les thèmes "AddNew Method", "Edit Method", "Delete Method", "Update Method", et "Updatable Property" dans DAO Help.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset

Construit un objet `CDaoRecordset`.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Paramètres

*base de pData*<br/>
Contient un pointeur à un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) ou la valeur NULL. Si ce n’est `Open` pas NULL et la fonction membre de l’objet `CDaoDatabase` n’a pas été appelé pour le connecter à la source de données, le recordet tente de l’ouvrir pour vous lors de son propre appel [Open.](#open) Si vous passez NULL, un `CDaoDatabase` objet est construit et connecté pour vous en utilisant `CDaoRecordset`les informations de source de données que vous avez spécifiées si vous avez dérivé votre classe de nombre d’enregistrements à partir de .

### <a name="remarks"></a>Notes

Vous pouvez `CDaoRecordset` soit utiliser directement ou tirer `CDaoRecordset`une classe spécifique à l’application de . Vous pouvez utiliser ClassWizard pour dériver vos classes de records.

> [!NOTE]
> Si vous `CDaoRecordset` dérivez une classe, votre classe dérivée doit fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur, `CDaoRecordset::CDaoRecordset`en passant les paramètres appropriés le long de lui.

Passez NULL à votre constructeur de `CDaoDatabase` records pour qu’un objet soit construit et connecté automatiquement pour vous. Il s’agit d’un raccourci utile qui `CDaoDatabase` ne vous oblige pas à construire et connecter un objet avant de construire votre ensemble d’enregistrements. Si `CDaoDatabase` l’objet n’est pas ouvert, un objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) sera également créé pour vous qui utilise l’espace de travail par défaut. Pour plus d’informations, voir [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

## <a name="cdaorecordsetclose"></a><a name="close"></a>CDaoRecordset::Fermer

La `CDaoRecordset` fermeture d’un objet le supprime de la collection d’enregistrements ouverts dans la base de données associée.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Parce `Close` que ne `CDaoRecordset` détruit pas l’objet, `Open` vous pouvez réutiliser l’objet en faisant appel à la même source de données ou à une source de données différente.

Toutes les instructions [AddNew](#addnew) ou [Edit](#edit) en attente sont annulées, et toutes les transactions en attente sont annulées. Si vous souhaitez préserver les ajouts ou les modifications en attente, appelez [Mise à jour](#update) avant d’appeler `Close` pour chaque ensemble d’enregistrements.

Vous pouvez `Open` appeler `Close`à nouveau après avoir appelé . Cela vous permet de réutiliser l’objet de l’enregistrement. Une meilleure alternative est d’appeler [Requery](#requery), si possible.

Pour obtenir des informations connexes, consultez le thème « Méthode de clôture » dans DAO Help.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a>CDaoRecordset::Delete

Appelez cette fonction de membre pour supprimer l’enregistrement actuel dans un objet de type dynaset ou de type table ouvert.

```
virtual void Delete();
```

### <a name="remarks"></a>Notes

Après une suppression réussie, les membres des données de terrain du recordet sont définis à une valeur nulle, et vous devez explicitement appeler l’une des fonctions des membres de navigation recordet ( [Déplacer](#move), [Chercher](#seek), [SetBookmark](#setbookmark), et ainsi de suite) afin de se déplacer hors de l’enregistrement supprimé. Lorsque vous supprimez les enregistrements d’un dossier, il doit `Delete`y avoir un enregistrement en cours dans le dossier avant d’appeler ; autrement, MFC jette une exception.

`Delete`supprime l’enregistrement actuel et le rend inaccessible. Bien que vous ne pouvez pas modifier ou utiliser l’enregistrement supprimé, il reste à jour. Une fois que vous passez à un autre enregistrement, cependant, vous ne pouvez pas rendre l’enregistrement supprimé en cours à nouveau.

> [!CAUTION]
> Le tableau de dossier doit être updatable et il doit y `Delete`avoir un courant d’enregistrement valide dans le dossier lorsque vous appelez . Par exemple, si vous supprimez un enregistrement mais ne `Delete` faites `Delete` pas défiler vers un nouvel enregistrement avant d’appeler à nouveau, lance un [CDaoException](../../mfc/reference/cdaoexception-class.md).

Vous pouvez undelete un enregistrement si vous utilisez des transactions et que vous appelez le [CDaoWorkspace:Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) fonction membre. Si le tableau de base est le tableau principal d’une relation de suppression en cascade, la suppression de l’enregistrement actuel peut également supprimer un ou plusieurs enregistrements dans un tableau étranger. Pour plus d’informations, voir la définition "cascade supprimer" dans DAO Help.

Contrairement `AddNew` `Edit`et , `Delete` un appel à n’est pas suivie d’un appel à `Update`.

Pour plus d’informations connexes, consultez les thèmes "AddNew Method", "Edit Method", "Delete Method", "Update Method", et "Updatable Property" dans DAO Help.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CDaoRecordset::DoFieldExchange

Le cadre appelle cette fonction membre pour échanger automatiquement des données entre les membres des données de champ de votre objet de numérotation et les colonnes correspondantes de l’enregistrement actuel sur la source de données.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Contient un pointeur d’un `CDaoFieldExchange` objet. Le cadre aura déjà mis en place cet objet pour spécifier un contexte pour l’opération d’échange sur le terrain.

### <a name="remarks"></a>Notes

Il lie également vos membres de données de paramètres, le cas échéant, aux paramètres des participants dans la chaîne de relevé SQL pour la sélection du recordet. L’échange de données sur le terrain, appelé DAO record field exchange (DFX), fonctionne dans les deux sens : des membres des données de terrain de l’objet de l’enregistrement aux champs de l’enregistrement sur la source de données, et de l’enregistrement sur la source de données à l’objet de l’enregistreur. Si vous êtes des colonnes de liaison `DoFieldExchange`dynamiquement, vous n’êtes pas tenu de mettre en œuvre .

La seule action que vous `DoFieldExchange` devez normalement prendre pour implémenter pour votre classe de recordet dérivé est de créer la classe avec ClassWizard et de spécifier les noms et les types de données des membres de données sur le terrain. Vous pouvez également ajouter du code à ce que ClassWizard écrit pour spécifier les membres des données de paramètres. Si tous les champs doivent être liés dynamiquement, cette fonction sera inactive à moins que vous spécifiiez les membres des données de paramètres.

Lorsque vous déclarez votre classe de disques dérivés avec `DoFieldExchange` ClassWizard, l’assistant vous écrit un remplacement, qui ressemble à l’exemple suivant :

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a>CDaoRecordset::Edit

Appelez cette fonction de membre pour permettre des modifications au dossier actuel.

```
virtual void Edit();
```

### <a name="remarks"></a>Notes

Une fois `Edit` que vous appelez la fonction membre, les modifications apportées aux champs de l’enregistrement actuel sont copiées dans le tampon de copie. Après avoir apporté les modifications `Update` souhaitées à l’enregistrement, appelez pour enregistrer vos modifications. `Edit`enregistre les valeurs des membres des données du recordet. Si vous `Edit`appelez, faites `Edit` des modifications, puis appelez à nouveau, les `Edit` valeurs de l’enregistrement sont restaurées à ce qu’elles étaient avant le premier appel.

> [!CAUTION]
> Si vous modifiez un enregistrement et effectuez ensuite `Update`toute opération qui se déplace vers un autre enregistrement sans appeler d’abord, vos modifications sont perdues sans avertissement. De plus, si vous fermez le dossier ou la base de données parente, votre enregistrement modifié est rejeté sans avertissement.

Dans certains cas, vous pouvez mettre à jour une colonne en la rendant nulle (ne contenant aucune donnée). Pour ce faire, appelez `SetFieldNull` avec un paramètre de TRUE pour marquer le champ Null; cela provoque également la mise à jour de la colonne. Si vous voulez qu’un champ soit écrit à la source `SetFieldDirty` de données même si sa valeur n’a pas changé, appelez avec un paramètre de TRUE. Cela fonctionne même si le champ avait la valeur Null.

Le cadre marque les données modifiées des membres des données sur le terrain pour s’assurer qu’ils seront écrits au dossier sur la source de données par le mécanisme d’échange de champs de disques DAO (DFX). Changer la valeur d’un champ définit généralement le champ sale automatiquement, de sorte que vous aurez rarement besoin d’appeler [SetFieldDirty](#setfielddirty) vous-même, mais vous voudrez peut-être parfois s’assurer que les colonnes seront explicitement mis à jour ou insérés quelle que soit la valeur dans le membre des données sur le terrain. Le mécanisme DFX utilise également **PSEUDO NULL**. Pour plus d’informations, voir [CDaoFieldExchange:m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si le mécanisme de double tampon n’est pas utilisé, alors changer la valeur du champ ne met pas automatiquement le champ comme sale. Dans ce cas, il sera nécessaire de mettre explicitement le champ sale. Le drapeau contenu dans [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) contrôle cette vérification automatique sur le terrain.

Lorsque l’objet de la liste enregistre est verrouillé de façon pessimiste `Edit` dans un environnement multiuscule, l’enregistrement reste verrouillé à partir du moment où la mise à jour est terminée. Si le jeu d’enregistrement est verrouillé avec optimisme, l’enregistrement est verrouillé et comparé à l’enregistrement pré-édité juste avant qu’il ne soit mis à jour dans la base de données. Si le dossier a `Edit`changé `Update` depuis que vous avez appelé, l’opération échoue et MFC jette une exception. Vous pouvez changer le `SetLockingMode`mode de verrouillage avec .

> [!NOTE]
> Le verrouillage optimiste est toujours utilisé sur les formats externes de base de données, tels que ODBC et l’ISAM installable.

Le dossier actuel reste `Edit`à jour après votre appel . Pour `Edit`appeler , il doit y avoir un dossier actuel. S’il n’y a pas d’enregistrement actuel ou si le jeu d’enregistrement ne fait pas référence à un objet de type table ouverte ou dynaset,et, une exception se produit. `Edit` L’appel `CDaoException` provoque un lancer dans les conditions suivantes :

- Aucun enregistrement actif.

- La base de données ou l’enregistrement est lu uniquement.

- Aucun champ dans le dossier n’est updatable.

- La base de données ou l’enregistrement a été ouvert pour une utilisation exclusive par un autre utilisateur.

- Un autre utilisateur a verrouillé la page contenant votre enregistrement.

Si la source de données prend `Edit` en charge les transactions, vous pouvez effectuer la partie d’appel d’une transaction. Notez que `CDaoWorkspace::BeginTrans` vous `Edit` devez appeler avant d’appeler et après l’ouverture du dossier. Notez également `CDaoWorkspace::CommitTrans` que l’appel `Update` n’est pas un substitut pour appeler pour terminer l’opération. `Edit` Pour plus d’informations `CDaoWorkspace`sur les transactions, voir classe .

Pour plus d’informations connexes, consultez les thèmes "AddNew Method", "Edit Method", "Delete Method", "Update Method", et "Updatable Property" dans DAO Help.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a>CDaoRecordset::FillCache

Appelez cette fonction de membre pour mettre en cache un nombre spécifié d’enregistrements de l’enregistrement.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Paramètres

*Psize*<br/>
Spécifie le nombre de lignes à remplir dans le cache. Si vous ometez ce paramètre, la valeur est déterminée par le paramètre de propriété CacheSize de l’objet DAO sous-jacent.

*pBookmark (en)*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) spécifiant un signet. Le cache est rempli à partir de l’enregistrement indiqué par ce signet. Si vous ometez ce paramètre, le cache est rempli à partir de l’enregistrement indiqué par la propriété CacheStart de l’objet DAO sous-jacent.

### <a name="remarks"></a>Notes

La mise en cache améliore les performances d’une application qui récupère ou récupère des données à partir d’un serveur distant. Un cache est l’espace dans la mémoire locale qui détient les données les plus récentes récupérées à partir du serveur sur l’hypothèse que les données seront probablement demandées à nouveau pendant que l’application est en cours d’exécution. Lorsque des données sont demandées, le moteur de base de données Microsoft Jet vérifie d’abord le cache pour les données plutôt que de les récupérer sur le serveur, ce qui prend plus de temps. L’utilisation de données de mise en cache sur des sources de données non-ODBC n’a aucun effet car les données ne sont pas enregistrées dans le cache.

Plutôt que d’attendre que le cache soit rempli d’enregistrements tels qu’ils sont `FillCache` récupérés, vous pouvez remplir explicitement le cache à tout moment en appelant la fonction membre. Il s’agit d’un `FillCache` moyen plus rapide de remplir le cache parce que récupère plusieurs enregistrements à la fois au lieu d’un à la fois. Par exemple, pendant que chaque écran des enregistrements est `FillCache` affiché, vous pouvez avoir votre appel d’application pour aller chercher le prochain écran des enregistrements.

Toute base de données ODBC accessible avec des objets de records peut avoir un cache local. Pour créer le cache, ouvrez un objet de l’ensemble `SetCacheStart` d’enregistrements à partir de la source de données à distance, puis appelez les fonctions et les `SetCacheSize` membres de l’ensemble d’enregistrements. Si *lSize* et *lBookmark* créent une plage qui est `SetCacheSize` `SetCacheStart`partiellement ou entièrement en dehors de la plage spécifiée par et, la partie de l’enregistrement en dehors de cette plage est ignorée et n’est pas chargée dans le cache. Si `FillCache` les demandes plus d’enregistrements que restent dans la source de données à distance, seuls les enregistrements restants sont récupérés, et aucune exception n’est lancée.

Les enregistrements récupérés dans le cache ne reflètent pas les modifications apportées simultanément aux données source par d’autres utilisateurs.

`FillCache`aller chercher seulement des enregistrements pas déjà mis en cache. Pour forcer une mise à jour de `SetCacheSize` toutes les données mises en cache, `SetCacheSize` appelez la fonction membre avec un paramètre *lSize* égal à 0, appelez à nouveau avec le paramètre *lSize* égal à la taille du cache que vous avez demandé à l’origine, puis appelez `FillCache`.

Pour plus d’informations connexes, voir le sujet "FillCache Method" dans DAO Aide.

## <a name="cdaorecordsetfind"></a><a name="find"></a>CDaoRecordset::Trouver

Appelez cette fonction de membre pour localiser une chaîne particulière dans un jeu d’enregistrement de type dynaset ou instantané à l’aide d’un opérateur de comparaison.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Paramètres

*lFindType (en)*<br/>
Une valeur indiquant le type d’opération Trouver souhaitée. Les valeurs possibles sont les suivantes :

- AFX_DAO_NEXT Trouvez le prochain emplacement d’une chaîne assortie.

- AFX_DAO_PREV Trouvez l’emplacement précédent d’une chaîne assortie.

- AFX_DAO_FIRST Trouvez le premier emplacement d’une chaîne assortie.

- AFX_DAO_LAST Trouvez le dernier emplacement d’une chaîne assortie.

*lpszFilter (lpszFilter)*<br/>
Une expression de chaîne (comme la clause **WHERE** dans une déclaration SQL sans le mot **Où**) utilisée pour localiser l’enregistrement. Par exemple :

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Valeur de retour

Nonzero si des enregistrements correspondants sont trouvés, sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez trouver la première, la prochaine, la précédente ou la dernière instance de la chaîne. `Find`est une fonction virtuelle, de sorte que vous pouvez l’emporter et ajouter votre propre implémentation. Les `FindFirst` `FindLast`fonctions , `FindNext`, `FindPrev` et `Find` membre appellent la `Find` fonction membre, de sorte que vous pouvez utiliser pour contrôler le comportement de toutes les opérations De trouver.

Pour localiser un enregistrement dans un jeu d’enregistrement de type table, appelez la fonction membre [Seek.](#seek)

> [!TIP]
> Plus l’ensemble des records que `Find` vous avez sera petit, plus il sera efficace. En général, et en particulier avec les données ODBC, il est préférable de créer une nouvelle requête qui récupère juste les enregistrements que vous voulez.

Pour plus d’informations connexes, voir le sujet "FindFirst, FindLast, FindNext, FindPrevious Methods" dans DAO Help.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a>CDaoRecordset::FindFirst

Appelez cette fonction de membre pour trouver le premier enregistrement qui correspond à une condition spécifiée.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Paramètres

*lpszFilter (lpszFilter)*<br/>
Une expression de chaîne (comme la clause **WHERE** dans une déclaration SQL sans le mot **Où**) utilisée pour localiser l’enregistrement.

### <a name="return-value"></a>Valeur de retour

Nonzero si des enregistrements correspondants sont trouvés, sinon 0.

### <a name="remarks"></a>Notes

La `FindFirst` fonction membre commence sa recherche depuis le début de l’enregistrement et les recherches jusqu’à la fin de l’enregistrement.

Si vous souhaitez inclure tous les enregistrements de votre recherche (pas seulement ceux qui répondent à une condition spécifique), utilisez l’une des opérations Move pour passer d’enregistrement en enregistrement. Pour localiser un enregistrement dans un jeu `Seek` d’enregistrement de type table, appelez la fonction membre.

Si un enregistrement correspondant aux critères n’est pas localisé, `FindFirst` le pointeur d’enregistrement actuel est indéterminé et renvoie zéro. Si le registre contient plus d’un enregistrement `FindFirst` qui répond aux `FindNext` critères, localise le premier événement, localise l’événement suivant, et ainsi de suite.

> [!CAUTION]
> Si vous modifiez l’enregistrement actuel, assurez-vous d’enregistrer les modifications en appelant la `Update` fonction membre avant de passer à un autre enregistrement. Si vous passez à un autre enregistrement sans mise à jour, vos modifications sont perdues sans avertissement.

Le `Find` membre fonctionne la recherche à partir de l’emplacement et dans la direction spécifiée dans le tableau suivant :

|Trouver des opérations|Begin|Direction de recherche|
|---------------------|-----------|----------------------|
|`FindFirst`|Début de recordset|Fin de l’enregistrement|
|`FindLast`|Fin de l’enregistrement|Début de recordset|
|`FindNext`|Enregistrement actuel|Fin de l’enregistrement|
|`FindPrevious`|Enregistrement actuel|Début de recordset|

> [!NOTE]
> Lorsque vous `FindLast`appelez, le moteur de base de données Microsoft Jet remplit entièrement votre dossier avant de commencer la recherche, si cela n’a pas déjà été fait. La première recherche peut prendre plus de temps que les recherches ultérieures.

L’utilisation de l’une des `MoveFirst` opérations `MoveNext`Find n’est pas la même chose que l’appel ou, cependant, qui rend simplement le premier ou le prochain courant d’enregistrement sans spécifier une condition. Vous pouvez suivre une opération Trouver avec une opération Move.

Gardez à l’esprit ce qui suit lors de l’utilisation des opérations Trouver :

- Si `Find` les déclarations non zéro, l’enregistrement actuel n’est pas défini. Dans ce cas, vous devez positionner le pointeur d’enregistrement actuel à un enregistrement valide.

- Vous ne pouvez pas utiliser une opération Trouver avec un livreur de type instantané défilant vers l’avant uniquement.

- Vous devez utiliser le format de date des États-Unis (année-journée) lorsque vous recherchez des champs contenant des dates, même si vous n’utilisez pas la version américaine du moteur de base de données Microsoft Jet; autrement, il se peut qu’il soit inauvable de faire correspondre les dossiers.

- Lorsque vous travaillez avec des bases de données ODBC et de grands dynasets, vous pouvez découvrir que l’utilisation des opérations Trouver est lente, en particulier lorsque vous travaillez avec de grands ensembles d’enregistrements. Vous pouvez améliorer vos performances en utilisant des requêtes SQL avec des `CDaoQuerydef` clauses **ORDERBY** personnalisées ou **WHERE,** des requêtes en paramètres ou des objets qui récupèrent des enregistrements indexés spécifiques.

Pour plus d’informations connexes, voir le sujet "FindFirst, FindLast, FindNext, FindPrevious Methods" dans DAO Help.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a>CDaoRecordset::FindLast

Appelez cette fonction de membre pour trouver le dernier enregistrement qui correspond à une condition spécifiée.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Paramètres

*lpszFilter (lpszFilter)*<br/>
Une expression de chaîne (comme la clause **WHERE** dans une déclaration SQL sans le mot **Où**) utilisée pour localiser l’enregistrement.

### <a name="return-value"></a>Valeur de retour

Nonzero si des enregistrements correspondants sont trouvés, sinon 0.

### <a name="remarks"></a>Notes

La `FindLast` fonction membre commence sa recherche à la fin de l’enregistrement et cherche vers l’arrière vers le début de l’enregistrement.

Si vous souhaitez inclure tous les enregistrements de votre recherche (pas seulement ceux qui répondent à une condition spécifique), utilisez l’une des opérations Move pour passer d’enregistrement en enregistrement. Pour localiser un enregistrement dans un jeu `Seek` d’enregistrement de type table, appelez la fonction membre.

Si un enregistrement correspondant aux critères n’est pas localisé, `FindLast` le pointeur d’enregistrement actuel est indéterminé et renvoie zéro. Si le registre contient plus d’un enregistrement `FindFirst` qui satisfait aux `FindNext` critères, localise le premier événement, localise l’événement suivant après le premier événement, et ainsi de suite.

> [!CAUTION]
> Si vous modifiez l’enregistrement actuel, assurez-vous d’enregistrer les modifications en appelant la `Update` fonction membre avant de passer à un autre enregistrement. Si vous passez à un autre enregistrement sans mise à jour, vos modifications sont perdues sans avertissement.

L’utilisation de l’une des `MoveFirst` opérations `MoveNext`Find n’est pas la même chose que l’appel ou, cependant, qui rend simplement le premier ou le prochain courant d’enregistrement sans spécifier une condition. Vous pouvez suivre une opération Trouver avec une opération Move.

Gardez à l’esprit ce qui suit lors de l’utilisation des opérations Trouver :

- Si `Find` les déclarations non zéro, l’enregistrement actuel n’est pas défini. Dans ce cas, vous devez positionner le pointeur d’enregistrement actuel à un enregistrement valide.

- Vous ne pouvez pas utiliser une opération Trouver avec un livreur de type instantané défilant vers l’avant uniquement.

- Vous devez utiliser le format de date des États-Unis (année-journée) lorsque vous recherchez des champs contenant des dates, même si vous n’utilisez pas la version américaine du moteur de base de données Microsoft Jet; autrement, il se peut qu’il soit inauvable de faire correspondre les dossiers.

- Lorsque vous travaillez avec des bases de données ODBC et de grands dynasets, vous pouvez découvrir que l’utilisation des opérations Trouver est lente, en particulier lorsque vous travaillez avec de grands ensembles d’enregistrements. Vous pouvez améliorer vos performances en utilisant des requêtes SQL avec des `CDaoQuerydef` clauses **ORDERBY** personnalisées ou **WHERE,** des requêtes en paramètres ou des objets qui récupèrent des enregistrements indexés spécifiques.

Pour plus d’informations connexes, voir le sujet "FindFirst, FindLast, FindNext, FindPrevious Methods" dans DAO Help.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a>CDaoRecordset::FindNext

Appelez cette fonction de membre pour trouver le prochain enregistrement qui correspond à une condition spécifiée.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Paramètres

*lpszFilter (lpszFilter)*<br/>
Une expression de chaîne (comme la clause **WHERE** dans une déclaration SQL sans le mot **Où**) utilisée pour localiser l’enregistrement.

### <a name="return-value"></a>Valeur de retour

Nonzero si des enregistrements correspondants sont trouvés, sinon 0.

### <a name="remarks"></a>Notes

La `FindNext` fonction membre commence sa recherche à l’enregistrement actuel et les recherches jusqu’à la fin de l’enregistrement.

Si vous souhaitez inclure tous les enregistrements de votre recherche (pas seulement ceux qui répondent à une condition spécifique), utilisez l’une des opérations Move pour passer d’enregistrement en enregistrement. Pour localiser un enregistrement dans un jeu `Seek` d’enregistrement de type table, appelez la fonction membre.

Si un enregistrement correspondant aux critères n’est pas localisé, `FindNext` le pointeur d’enregistrement actuel est indéterminé et renvoie zéro. Si le registre contient plus d’un enregistrement `FindFirst` qui répond aux `FindNext` critères, localise le premier événement, localise l’événement suivant, et ainsi de suite.

> [!CAUTION]
> Si vous modifiez l’enregistrement actuel, assurez-vous d’enregistrer les modifications en appelant la `Update` fonction membre avant de passer à un autre enregistrement. Si vous passez à un autre enregistrement sans mise à jour, vos modifications sont perdues sans avertissement.

L’utilisation de l’une des `MoveFirst` opérations `MoveNext`Find n’est pas la même chose que l’appel ou, cependant, qui rend simplement le premier ou le prochain courant d’enregistrement sans spécifier une condition. Vous pouvez suivre une opération Trouver avec une opération Move.

Gardez à l’esprit ce qui suit lors de l’utilisation des opérations Trouver :

- Si `Find` les déclarations non zéro, l’enregistrement actuel n’est pas défini. Dans ce cas, vous devez positionner le pointeur d’enregistrement actuel à un enregistrement valide.

- Vous ne pouvez pas utiliser une opération Trouver avec un livreur de type instantané défilant vers l’avant uniquement.

- Vous devez utiliser le format de date des États-Unis (année-journée) lorsque vous recherchez des champs contenant des dates, même si vous n’utilisez pas la version américaine du moteur de base de données Microsoft Jet; autrement, il se peut qu’il soit inauvable de faire correspondre les dossiers.

- Lorsque vous travaillez avec des bases de données ODBC et de grands dynasets, vous pouvez découvrir que l’utilisation des opérations Trouver est lente, en particulier lorsque vous travaillez avec de grands ensembles d’enregistrements. Vous pouvez améliorer vos performances en utilisant des requêtes SQL avec des `CDaoQuerydef` clauses **ORDERBY** personnalisées ou **WHERE,** des requêtes en paramètres ou des objets qui récupèrent des enregistrements indexés spécifiques.

Pour plus d’informations connexes, voir le sujet "FindFirst, FindLast, FindNext, FindPrevious Methods" dans DAO Help.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a>CDaoRecordset::FindPrev

Appelez cette fonction de membre pour trouver l’enregistrement précédent qui correspond à une condition spécifiée.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Paramètres

*lpszFilter (lpszFilter)*<br/>
Une expression de chaîne (comme la clause **WHERE** dans une déclaration SQL sans le mot **Où**) utilisée pour localiser l’enregistrement.

### <a name="return-value"></a>Valeur de retour

Nonzero si des enregistrements correspondants sont trouvés, sinon 0.

### <a name="remarks"></a>Notes

La `FindPrev` fonction membre commence sa recherche à l’enregistrement actuel et cherche vers l’arrière vers le début de l’enregistrement.

Si vous souhaitez inclure tous les enregistrements de votre recherche (pas seulement ceux qui répondent à une condition spécifique), utilisez l’une des opérations Move pour passer d’enregistrement en enregistrement. Pour localiser un enregistrement dans un jeu `Seek` d’enregistrement de type table, appelez la fonction membre.

Si un enregistrement correspondant aux critères n’est pas localisé, `FindPrev` le pointeur d’enregistrement actuel est indéterminé et renvoie zéro. Si le registre contient plus d’un enregistrement `FindFirst` qui répond aux `FindNext` critères, localise le premier événement, localise l’événement suivant, et ainsi de suite.

> [!CAUTION]
> Si vous modifiez l’enregistrement actuel, assurez-vous d’enregistrer les modifications en appelant la `Update` fonction membre avant de passer à un autre enregistrement. Si vous passez à un autre enregistrement sans mise à jour, vos modifications sont perdues sans avertissement.

L’utilisation de l’une des `MoveFirst` opérations `MoveNext`Find n’est pas la même chose que l’appel ou, cependant, qui rend simplement le premier ou le prochain courant d’enregistrement sans spécifier une condition. Vous pouvez suivre une opération Trouver avec une opération Move.

Gardez à l’esprit ce qui suit lors de l’utilisation des opérations Trouver :

- Si `Find` les déclarations non zéro, l’enregistrement actuel n’est pas défini. Dans ce cas, vous devez positionner le pointeur d’enregistrement actuel à un enregistrement valide.

- Vous ne pouvez pas utiliser une opération Trouver avec un livreur de type instantané défilant vers l’avant uniquement.

- Vous devez utiliser le format de date des États-Unis (année-journée) lorsque vous recherchez des champs contenant des dates, même si vous n’utilisez pas la version américaine du moteur de base de données Microsoft Jet; autrement, il se peut qu’il soit inauvable de faire correspondre les dossiers.

- Lorsque vous travaillez avec des bases de données ODBC et de grands dynasets, vous pouvez découvrir que l’utilisation des opérations Trouver est lente, en particulier lorsque vous travaillez avec de grands ensembles d’enregistrements. Vous pouvez améliorer vos performances en utilisant des requêtes SQL avec des `CDaoQuerydef` clauses **ORDERBY** personnalisées ou **WHERE,** des requêtes en paramètres ou des objets qui récupèrent des enregistrements indexés spécifiques.

Pour plus d’informations connexes, voir le sujet "FindFirst, FindLast, FindNext, FindPrevious Methods" dans DAO Help.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>CDaoRecordset::GetAbsolutePosition

Retourne le nombre record de l’enregistrement actuel d’un objet de recordet.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Valeur de retour

Un intégrier de 0 au nombre d’enregistrements dans le dossier. Correspond à la position ordinaire du dossier actuel dans le dossier.

### <a name="remarks"></a>Notes

La valeur de propriété AbsolutePosition de l’objet DAO sous-jacent est basée à zéro; un réglage de 0 se réfère au premier enregistrement dans le record. Vous pouvez déterminer le nombre d’enregistrements peuplés dans le dossier en appelant [GetRecordCount](#getrecordcount). Les `GetRecordCount` appels peuvent prendre un certain temps parce qu’il doit accéder à tous les dossiers pour déterminer le nombre.

S’il n’y a pas d’enregistrement actuel, comme lorsqu’il n’y a pas d’enregistrements dans le dossier, - 1 est retourné. Si l’enregistrement actuel est supprimé, la valeur de la propriété AbsolutePosition n’est pas définie, et MFC lance une exception si elle est référencée. Pour les enregistrements de type dynaset, de nouveaux enregistrements sont ajoutés à la fin de la séquence.

> [!NOTE]
> Cette propriété n’est pas destinée à être utilisée comme un numéro de dossier de substitution. Les signets sont toujours le moyen recommandé de conserver et de revenir à une position donnée et sont le seul moyen de positionner l’enregistrement actuel sur tous les types d’objets de la liste. En particulier, la position d’un enregistrement donné change lorsque l’enregistrement(s) qui le précède est supprimé. Rien ne garantit non plus qu’un dossier donné aura la même position absolue si le dossier est recréé à nouveau parce que l’ordre des enregistrements individuels dans un dossier n’est pas garanti à moins qu’il ne soit créé avec une déclaration SQL à l’aide d’une clause **ORDERBY.**

> [!NOTE]
> Cette fonction de membre n’est valable que pour les enregistrements de type dynaset et instantanés.

Pour obtenir des informations connexes, consultez le thème « AbsolutePosition Property » dans DAO Help.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>CDaoRecordset::GetBookmark

Appelez cette fonction de membre pour obtenir la valeur de signet dans un enregistrement particulier.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur représentant le signet de l’enregistrement actuel.

### <a name="remarks"></a>Notes

Lorsqu’un objet de la collection d’enregistrements est créé ou ouvert, chacun de ses disques a déjà un signet unique s’il les prend en charge. Appelez `CanBookmark` pour déterminer si un carnet prend en charge les signets.

Vous pouvez enregistrer le signet de l’enregistrement actuel en `COleVariant` attribuant la valeur du signet à un objet. Pour revenir rapidement à cet enregistrement à tout moment `SetBookmark` après avoir déménagé à `COleVariant` un enregistrement différent, appelez avec un paramètre correspondant à la valeur de cet objet.

> [!NOTE]
> Appeler [Requery](#requery) change les signets DAO.

Pour plus d’informations connexes, consultez le thème "Bookmark Property" dans DAO Help.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>CDaoRecordset::GetCacheSize

Appelez cette fonction de membre pour obtenir le nombre d’enregistrements mis en cache.

```
long GetCacheSize();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui spécifie le nombre d’enregistrements dans un ensemble d’enregistrements de type dynaset contenant des données à mettre en cache localement à partir d’une source de données ODBC.

### <a name="remarks"></a>Notes

La mise en cache de données améliore les performances d’une application qui récupère les données d’un serveur distant grâce à des objets de type album de type dynaset. Un cache est un espace de mémoire locale qui détient les données les plus récemment récupérées sur le serveur dans le cas où les données seront demandées à nouveau pendant que l’application est en cours d’exécution. Lorsque des données sont demandées, le moteur de base de données Microsoft Jet vérifie d’abord le cache pour les données demandées plutôt que de les récupérer à partir du serveur, ce qui prend plus de temps. Les données qui ne proviennent pas d’une source de données ODBC ne sont pas enregistrées dans le cache.

Toute source de données ODBC, telle qu’une table jointe, peut avoir un cache local.

Pour plus d’informations connexes, consultez le thème "CacheSize, CacheStart Properties" dans DAO Help.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>CDaoRecordset::GetCacheStart

Appelez cette fonction de membre pour obtenir la valeur de signet du premier enregistrement dans le livre d’enregistrement à mettre en cache.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Valeur de retour

Un `COleVariant` qui spécifie le signet du premier enregistrement dans le livre d’enregistrement à mettre en cache.

### <a name="remarks"></a>Notes

Le moteur de base de données Microsoft Jet demande des enregistrements dans la gamme de caches à partir du cache, et il demande des enregistrements en dehors de la gamme de cache du serveur.

> [!NOTE]
> Les enregistrements récupérés dans le cache ne reflètent pas les modifications apportées simultanément aux données source par d’autres utilisateurs.

Pour plus d’informations connexes, consultez le thème "CacheSize, CacheStart Properties" dans DAO Help.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex

Appelez cette fonction de membre pour déterminer l’index `CDaoRecordset` actuellement utilisé dans un objet indexé de type table.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Valeur de retour

A `CString` contenant le nom de l’index actuellement utilisé avec un tableau de type enregistrements. Retourne une chaîne vide si aucun index n’a été défini.

### <a name="remarks"></a>Notes

Cet index est la base de la commande d’enregistrements dans un jeu d’enregistrement de type table, et est utilisé par la fonction membre [Seek](#seek) pour localiser les enregistrements.

Un `CDaoRecordset` objet peut avoir plus d’un indice, mais ne peut utiliser qu’un seul indice à la fois (bien qu’un objet [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) puisse avoir plusieurs index définis sur celui-ci).

Pour obtenir des informations connexes, consultez le thème « Objet indiciel » et la définition « indice actuel » dans DAO Help.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>CDaoRecordset::GetDateCreated

Appelez cette fonction de membre pour récupérer la date et l’heure qu’une table de base a été créée.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valeur de retour

Un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant la date et l’heure de la création de la table de base.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée.

Pour plus d’informations connexes, voir le sujet "DateCreated, LastUpdated Properties" dans DAO Help.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated

Appelez cette fonction de membre pour récupérer la date et l’heure où le schéma a été mis à jour pour la dernière fois.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valeur de retour

Un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant la date et l’heure de la structure de la table de base (schéma) a été mis à jour pour la dernière fois.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la structure de la table de base (schéma) a été mise à jour pour la dernière fois.

Pour plus d’informations connexes, voir le sujet "DateCreated, LastUpdated Properties" dans DAO Help.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName

Appelez cette fonction de membre pour déterminer le nom de la base de données pour ce jeu d’enregistrement.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient le chemin et le nom de la base de données à partir de laquelle ce jeu d’enregistrement est dérivé.

### <a name="remarks"></a>Notes

Si un jeu d’enregistrement est créé sans pointeur sur une [base de CDaoData,](../../mfc/reference/cdaodatabase-class.md)alors ce chemin est utilisé par le jeu d’enregistrement pour ouvrir la base de données par défaut. Par défaut, cette fonction renvoie une chaîne vide. Lorsque ClassWizard tire un nouveau `CDaoRecordset`groupe d’enregistrements de , il va créer cette fonction pour vous.

L’exemple suivant illustre l’utilisation du\\\\double backslash ( ) dans la chaîne, comme il est nécessaire pour que la chaîne soit interprétée correctement.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL

Le cadre appelle cette fonction membre pour obtenir la déclaration SQL par défaut sur laquelle le dossier est basé.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient la déclaration SQL par défaut.

### <a name="remarks"></a>Notes

Il peut s’agir d’un nom de table ou d’une déclaration **SQL SELECT.**

Vous définissez indirectement la déclaration SQL par défaut en déclarant votre classe de disques avec ClassWizard, et ClassWizard effectue cette tâche pour vous.

Si vous passez une corde SQL nulle à [l’ouverture](#open), alors cette fonction est appelée pour déterminer le nom de table ou SQL pour votre dossier.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>CDaoRecordset::GetEditMode

Appelez cette fonction membre pour déterminer l’état de l’édition, qui est l’une des valeurs suivantes :

```
short GetEditMode();
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur qui indique l’état d’édition de l’enregistrement actuel.

### <a name="remarks"></a>Notes

|Valeur|Description|
|-----------|-----------------|
|`dbEditNone`|Aucune opération d’édition n’est en cours.|
|`dbEditInProgress`|`Edit` a été appelé.|
|`dbEditAdd`|`AddNew` a été appelé.|

Pour plus d’informations connexes, consultez le sujet "EditMode Property" dans DAO Help.

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>CDaoRecordset::GetFieldCount

Appelez cette fonction de membre pour récupérer le nombre de champs (colonnes) définis dans l’enregistrement.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de champs dans le dossier.

### <a name="remarks"></a>Notes

Pour obtenir des renseignements connexes, consultez le thème « Count Property » dans DAO Help.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo

Appelez cette fonction de membre pour obtenir des informations sur les champs dans un jeu d’enregistrement.

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice zéro du champ prédéfini dans la collection Fields du recordet, pour le lookup par index.

*Fieldinfo*<br/>
Une référence à une structure [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoOptions*<br/>
Options qui spécifient les informations sur l’enregistrement à récupérer. Les options disponibles sont énumérées ici avec ce qu’elles causent le retour de la fonction. Pour obtenir de meilleures performances, ne récupérez que le niveau d’information dont vous avez besoin :

- `AFX_DAO_PRIMARY_INFO`(Par défaut) Nom, Type, Taille, Attributs

- `AFX_DAO_SECONDARY_INFO`Informations primaires, plus: Position ordinaire, Requise, Permettre la longueur zéro, Ordonnance de collating, Nom étranger, Champ source, Tableau source

- `AFX_DAO_ALL_INFO`Informations primaires et secondaires, plus : Valeur par défaut, règle de validation, texte de validation

*lpszName (en)*<br/>
Nom du champ.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un champ par index. L’autre version vous permet de rechercher un champ par son nom.

Pour une description de l’information retournée, voir la structure [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez des informations pour tous les niveaux antérieurs ainsi.

Pour obtenir des renseignements connexes, consultez le thème « Propriété d’attributs » dans DAO Help.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CDaoRecordset::GetFieldValue

Appelez cette fonction de membre pour récupérer des données dans un jeu d’enregistrement.

```
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une chaîne qui contient le nom d’un champ.

*varValue*<br/>
Une référence `COleVariant` à un objet qui stockera la valeur d’un champ.

*nIndex*<br/>
Un index zéro du champ dans la collection Fields du recordet, pour la recherche par index.

### <a name="return-value"></a>Valeur de retour

Les deux versions de `GetFieldValue` ce retour d’une valeur renvoient un objet [COleVariant](../../mfc/reference/colevariant-class.md) qui contient la valeur d’un champ.

### <a name="remarks"></a>Notes

Vous pouvez rechercher un champ par nom ou par position ordinaire.

> [!NOTE]
> Il est plus efficace d’appeler l’une des `COleVariant` versions de cette fonction de membre qui `COleVariant` prend une référence d’objet comme un paramètre, plutôt que d’appeler une version qui renvoie un objet. Les dernières versions de cette fonction sont conservées pour la compatibilité vers l’arrière.

Utilisez `GetFieldValue` et [SetFieldValue](#setfieldvalue) pour lier dynamiquement les champs au moment de l’exécution plutôt que les colonnes statiquement contraignantes à l’aide du mécanisme [DoFieldExchange.](#dofieldexchange)

`GetFieldValue`et `DoFieldExchange` le mécanisme peut être combiné pour améliorer les performances. Par exemple, `GetFieldValue` utilisez-le pour récupérer une valeur dont vous n’avez besoin qu’à la demande et attribuez cet appel à un bouton « Plus d’informations » dans l’interface.

Pour obtenir des renseignements connexes, consultez les thèmes « Objet de terrain » et « Propriété de valeur » dans DAO Help.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>CDaoRecordset::GetIndexCount

Appelez cette fonction de membre pour déterminer le nombre d’index disponibles sur l’enregistrement de type table.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’index dans l’enregistrement de type table.

### <a name="remarks"></a>Notes

`GetIndexCount`est utile pour boucler tous les index dans le livre d’enregistrement. À cette fin, utiliser `GetIndexCount` en conjonction avec [GetIndexInfo](#getindexinfo). Si vous appelez cette fonction de membre sur des enregistrements de type dynaset ou instantanés, MFC lance une exception.

Pour obtenir des renseignements connexes, consultez le thème « Propriété d’attributs » dans DAO Help.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo

Appelez cette fonction de membre pour obtenir divers types d’information sur un index défini dans le tableau de base sous-jacent à un jeu d’enregistrement.

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice zéro dans la collection d’indices du tableau, pour la recherche par position numérique.

*indexinfo*<br/>
Une référence à une structure [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoOptions*<br/>
Options qui spécifient les informations sur l’index à récupérer. Les options disponibles sont énumérées ici avec ce qu’elles causent le retour de la fonction. Pour obtenir de meilleures performances, ne récupérez que le niveau d’information dont vous avez besoin :

- `AFX_DAO_PRIMARY_INFO`(Par défaut) Nom, Field Info, Fields

- `AFX_DAO_SECONDARY_INFO`Informations primaires, plus: Primaire, Unique, Clustered, IgnoreNulls, Requis, Étranger

- `AFX_DAO_ALL_INFO`Informations primaires et secondaires, plus : Nombre distinct

*lpszName (en)*<br/>
Un pointeur sur le nom de l’objet de l’index, pour le lookup par nom.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un index par sa position dans la collection. L’autre version vous permet de rechercher un index par nom.

Pour une description de l’information retournée, voir la structure [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez des informations pour tous les niveaux antérieurs ainsi.

Pour obtenir des renseignements connexes, consultez le thème « Propriété d’attributs » dans DAO Help.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark

Appelez cette fonction de membre pour récupérer le signet de l’enregistrement le plus récemment ajouté ou mis à jour.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Valeur de retour

Un `COleVariant` signet contenant le livreur qui indique l’enregistrement le plus récemment ajouté ou modifié.

### <a name="remarks"></a>Notes

Lorsqu’un objet de la collection d’enregistrements est créé ou ouvert, chacun de ses disques a déjà un signet unique s’il les prend en charge. Appelez [GetBookmark](#getbookmark) pour déterminer si le jeu d’enregistrement prend en charge les signets. Si le livreur ne prend pas `CDaoException` en charge les signets, un est jeté.

Lorsque vous ajoutez un enregistrement, il apparaît à la fin de l’enregistrement, et n’est pas le record actuel. Pour que le nouvel `GetLastModifiedBookmark` enregistrement se `SetBookmark` compose, appelez et appelez ensuite pour revenir à l’enregistrement nouvellement ajouté.

Pour plus d’informations connexes, voir le thème "LastModified Property" dans DAO Help.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>CDaoRecordset::GetLockingMode

Appelez cette fonction de membre pour déterminer le type de verrouillage en vigueur pour l’enregistrement.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le type de verrouillage est pessimiste, sinon 0 pour le verrouillage des dossiers optimistes.

### <a name="remarks"></a>Notes

Lorsque le verrouillage pessimiste est en vigueur, la page de données contenant l’enregistrement que vous modifiez est verrouillée dès que vous appelez la fonction membre [Edit.](#edit) La page est déverrouillée lorsque vous appelez la fonction [De membre De mise à jour](#update) ou [close](#close) ou l’une des opérations Move or Find.

Lorsque le verrouillage optimiste est en vigueur, la page de données contenant `Update` l’enregistrement n’est verrouillée que pendant que l’enregistrement est mis à jour avec la fonction du membre.

Lorsque vous travaillez avec les sources de données ODBC, le mode de verrouillage est toujours optimiste.

Pour obtenir des informations connexes, consultez les thèmes « LockEdits Property » et « Locking Behavior in Multiuser Applications » dans DAO Help.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a>CDaoRecordset::GetName

Appelez cette fonction de membre pour récupérer le nom de l’enregistrement.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

A `CString` contenant le nom de l’enregistrement.

### <a name="remarks"></a>Notes

Le nom du jeu d’enregistrement doit commencer par une lettre et peut contenir un maximum de 40 caractères. Il peut inclure des nombres et des personnages de souligner, mais ne peut pas inclure la ponctuation ou des espaces.

Pour obtenir des informations connexes, consultez le thème « Propriété du nom » dans DAO Help.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>CDaoRecordset::GetParamValue

Appelez cette fonction de membre pour récupérer la valeur actuelle du paramètre spécifié stocké dans l’objet DAOParameter sous-jacent.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
La position numérique du paramètre dans l’objet DAOParameter sous-jacent.

*lpszName (en)*<br/>
Le nom du paramètre dont vous voulez la valeur.

### <a name="return-value"></a>Valeur de retour

Un objet de classe [COleVariant](../../mfc/reference/colevariant-class.md) qui contient la valeur du paramètre.

### <a name="remarks"></a>Notes

Vous pouvez accéder au paramètre par son nom ou par sa position numérique dans la collection.

Pour plus d’informations connexes, consultez le thème " Objet paramètre " dans DAO Help.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>CDaoRecordset::GetPercentPosition

Lorsque vous travaillez avec un jeu d’enregistrement de type `GetPercentPosition` dynaset ou instantané, si vous appelez avant de remplir complètement le jeu d’enregistrement, la quantité de mouvement est relative au nombre d’enregistrements consultés comme indiqué en appelant [GetRecordCount](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Valeur de retour

Un nombre entre 0 et 100 qui indique l’emplacement approximatif de l’enregistrement actuel dans l’objet de l’enregistrement en fonction d’un pourcentage des enregistrements dans le dossier.

### <a name="remarks"></a>Notes

Vous pouvez passer au dernier record en appelant [MoveLast](#movelast) pour compléter la population de tous les ensembles d’enregistrements, mais cela peut prendre beaucoup de temps.

Vous pouvez `GetPercentPosition` faire appel aux trois types d’objets de l’ensemble d’enregistrements, y compris les tableaux sans index. Toutefois, vous `GetPercentPosition` ne pouvez pas faire appel à des instantanés défilements avant-seulement, ou sur un enregistrement ouvert à partir d’une requête de passage contre une base de données externe. S’il n’y a pas d’enregistrement actuel, ou s’il enregistre actuel a été supprimé, un `CDaoException` est jeté.

Pour obtenir des renseignements connexes, consultez le thème « Propriété de pourcentage » dans DAO Help.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>CDaoRecordset::GetRecordCount

Appelez cette fonction de membre pour savoir combien d’enregistrements dans un dossier ont été consultés.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’enregistrements accessibles dans un objet de recordet.

### <a name="remarks"></a>Notes

`GetRecordCount`n’indique pas combien d’enregistrements sont contenus dans un ensemble d’enregistrements de type dynaset ou instantané jusqu’à ce que tous les enregistrements aient été consultés. Cet appel de fonction de membre peut prendre beaucoup de temps à remplir.

Une fois le dernier enregistrement consulté, la valeur de retour indique le nombre total d’enregistrements non supprimés dans l’ensemble d’enregistrements. Pour forcer l’accès au dernier `MoveLast` enregistrement, appelez la fonction ou `FindLast` le membre de l’enregistrement. Vous pouvez également utiliser un compte SQL pour déterminer le nombre approximatif d’enregistrements que votre requête retournera.

Lorsque votre application supprime les enregistrements dans un jeu d’enregistrement `GetRecordCount` de type dynaset, la valeur de rendement diminue. Toutefois, les enregistrements supprimés par d’autres utilisateurs ne sont pas reflétés jusqu’à `GetRecordCount` ce que l’enregistrement actuel soit positionné sur un enregistrement supprimé. Si vous exécutez une transaction qui affecte le `GetRecordCount` nombre d’enregistrements et qui a par la suite fait reculer la transaction, ne reflétera pas le nombre réel d’enregistrements restants.

La valeur `GetRecordCount` d’un enregistrement de type instantané n’est pas affectée par les changements dans les tableaux sous-jacents.

La valeur `GetRecordCount` d’un ensemble d’enregistrements de type table reflète le nombre approximatif d’enregistrements dans le tableau et est affectée immédiatement au fur et à mesure que les enregistrements de table sont ajoutés et supprimés.

Un enregistrement sans dossiers rapporte une valeur de 0. Lorsque vous travaillez avec des tables `GetRecordCount` jointes ou des bases de données ODBC, retourne toujours - 1. Appeler `Requery` la fonction du membre sur un `GetRecordCount` enregistrement réinitialise la valeur de tout comme si la requête avait été réécutée.

Pour obtenir des renseignements connexes, consultez le thème « RecordCount Property » dans DAO Help.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a>CDaoRecordset::GetSQL

Appelez cette fonction de membre pour obtenir la déclaration SQL qui a été utilisée pour sélectionner les dossiers du dossier lors de son ouverture.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient la déclaration SQL.

### <a name="remarks"></a>Notes

Il s’agira généralement d’une déclaration **SQL SELECT.**

La chaîne `GetSQL` retournée par est généralement différente de n’importe quelle chaîne que vous pouvez avoir passé à l’ensemble d’enregistrements dans le paramètre *lpszSQL* à la fonction membre [Open.](#open) C’est parce que le document construit une déclaration SQL complète basée sur ce que vous avez passé à `Open`, ce que vous avez spécifié avec ClassWizard, et ce que vous avez peut-être spécifié dans le [m_strFilter](#m_strfilter) et [m_strSort](#m_strsort) les membres des données.

> [!NOTE]
> Appelez cette fonction de `Open`membre seulement après avoir appelé .

Pour plus d’informations connexes, consultez le thème « Propriété SQL » dans DAO Aide.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a>CDaoRecordset::GetType

Appelez cette fonction de membre après l’ouverture de l’ensemble d’enregistrements pour déterminer le type de l’objet de l’enregistrement.

```
short GetType();
```

### <a name="return-value"></a>Valeur de retour

L’une des valeurs suivantes qui indique le type d’enregistrement :

- `dbOpenTable`Dossiers de type table

- `dbOpenDynaset`Dossiers de type Dynaset

- `dbOpenSnapshot`Enregistrement de type instantané

### <a name="remarks"></a>Notes

Pour obtenir des renseignements connexes, consultez le thème « Type Property » dans DAO Help.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule

Appelez cette fonction de membre pour déterminer la règle utilisée pour valider les données.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet contenant une valeur qui valide les données dans un enregistrement au fur et à mesure qu’elles sont modifiées ou ajoutées à un tableau.

### <a name="remarks"></a>Notes

Cette règle est basée sur le texte et est appliquée chaque fois que le tableau sous-jacent est modifié. Si les données ne sont pas légales, MFC lance une exception. Le message d’erreur retourné est le texte de la propriété ValidationText de l’objet de champ sous-jacent, si spécifié, ou le texte de l’expression spécifiée par la propriété ValidationRule de l’objet de champ sous-jacent. Vous pouvez appeler [GetValidationText](#getvalidationtext) pour obtenir le texte du message d’erreur.

Par exemple, un champ dans un dossier qui exige le jour du mois peut avoir une règle de validation telle que "JOUR BETWEEN 1 ET 31."

Pour plus d’informations, consultez le thème "ValidationRule Property" dans DAO Help.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoRecordset::GetValidationText

Appelez cette fonction de membre pour récupérer le texte de la propriété ValidationText de l’objet de champ sous-jacent.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet contenant le texte du message qui s’affiche si la valeur d’un champ ne satisfait pas à la règle de validation de l’objet de champ sous-jacent.

### <a name="remarks"></a>Notes

Pour plus d’informations connexes, consultez le thème "ValidationText Property" dans DAO Help.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a>CDaoRecordset::IsBOF

Appelez cette fonction de membre avant de faire défiler de l’enregistrement à l’enregistrement pour savoir si vous êtes allé avant le premier enregistrement de l’enregistrement.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet ne contient pas d’enregistrements ou si vous avez fait défiler vers l’arrière avant le premier enregistrement; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez `IsBOF` également `IsEOF` appeler avec pour déterminer si le jeu d’enregistrement contient des enregistrements ou est vide. Immédiatement après `Open`votre appel, si le `IsBOF` recordet ne contient pas d’enregistrements, renvoie nonzero. Lorsque vous ouvrez un record qui a au moins un `IsBOF` enregistrement, le premier enregistrement est le record actuel et retourne 0.

Si le premier enregistrement est l’enregistrement actuel et que vous appelez, `MovePrev` `IsBOF` retournera par la suite nonzero. Si `IsBOF` les retours nonzero et vous appelez `MovePrev`, une exception est lancée. Si `IsBOF` les déclarations non zéro, le dossier actuel n’est pas défini, et toute action qui nécessite un enregistrement actuel entraînera une exception.

Effet de méthodes `IsBOF` `IsEOF` spécifiques sur et paramètres :

- Appeler `Open*` en interne fait le premier enregistrement dans `MoveFirst`le record actuel en appelant . Par conséquent, faire appel `Open` à `IsBOF` `IsEOF` un ensemble vide de causes de records et de retourner nonzero. (Voir le tableau suivant pour `MoveFirst` le `MoveLast` comportement d’un échec ou d’un appel.)

- Toutes les opérations Move qui `IsBOF` réussissent `IsEOF` à localiser un dossier causent à la fois et au retour 0.

- Un `AddNew` appel suivi `Update` d’un appel qui insère avec succès un nouvel enregistrement entraînera le `IsBOF` retour 0, mais seulement si `IsEOF` elle n’est déjà pas zéro. L’état `IsEOF` de volonté restera toujours inchangé. Tel que défini par le moteur de base de données Microsoft Jet, le pointeur d’enregistrement actuel d’un jeu de disques vide est à la fin d’un fichier, de sorte que tout nouvel enregistrement est inséré après l’enregistrement actuel.

- Tout `Delete` appel, même s’il supprime le seul enregistrement restant d’un enregistrement, ne changera pas la valeur de `IsBOF` ou `IsEOF`.

Ce tableau montre quelles opérations De déménagement `IsBOF` /  `IsEOF`sont autorisées avec différentes combinaisons de .

||MoveFirst, MoveLast|MovePrev,<br /><br /> Déplacer < 0|Déplacer 0|Movenext<br /><br /> Déplacer > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`Nonzero,<br /><br /> `IsEOF`=0|Autorisé|Exception|Exception|Autorisé|
|`IsBOF`=0,<br /><br /> `IsEOF`Nonzero|Autorisé|Autorisé|Exception|Exception|
|Les deux nonzero|Exception|Exception|Exception|Exception|
|Les deux 0|Autorisé|Autorisé|Autorisé|Autorisé|

Permettre une opération Move ne signifie pas que l’opération permettra de localiser avec succès un enregistrement. Il indique simplement qu’une tentative d’effectuer l’opération De déménagement spécifiée est autorisée et ne générera pas d’exception. La valeur `IsBOF` des `IsEOF` fonctions et des fonctions des membres peut changer à la suite de la tentative de déménagement.

L’effet des opérations De mouvement qui ne `IsBOF` `IsEOF` trouvent pas d’enregistrement sur la valeur et les paramètres est indiqué dans le tableau suivant.

||IsBOF (isBOF)|IsEOF (IsEOF)|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nonzero (Nonzero)|Nonzero (Nonzero)|
|`Move` 0|Aucun changement|Aucun changement|
|`MovePrev`, `Move` < 0|Nonzero (Nonzero)|Aucun changement|
|`MoveNext`, `Move` > 0|Aucun changement|Nonzero (Nonzero)|

Pour plus d’informations connexes, voir le thème "BOF, EOF Properties" dans DAO Help.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a>CDaoRecordset::IsDeleted

Appelez cette fonction de membre pour déterminer si l’enregistrement actuel a été supprimé.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet est positionné sur un enregistrement supprimé; sinon 0.

### <a name="remarks"></a>Notes

Si vous faites défiler vers un enregistrement et `IsDeleted` retourne TRUE (nonzero), alors vous devez faire défiler vers un autre enregistrement avant de pouvoir effectuer d’autres opérations de nombre d’enregistrements.

> [!NOTE]
> Vous n’avez pas besoin de vérifier l’état supprimé pour les enregistrements dans un jeu d’enregistrement instantané ou de type table. Étant donné que les enregistrements ne peuvent pas `IsDeleted`être supprimés d’un instantané, il n’est pas nécessaire d’appeler . Pour les enregistrements de type table, les enregistrements supprimés sont en fait supprimés de l’ensemble d’enregistrements. Une fois qu’un enregistrement a été supprimé, soit par vous, un autre utilisateur, soit dans un autre album, vous ne pouvez pas revenir à cet enregistrement. Par conséquent, il n’est pas nécessaire d’appeler `IsDeleted`.

Lorsque vous supprimez un enregistrement d’un dynaset, il est supprimé de l’ensemble d’enregistrements et vous ne pouvez pas faire défiler vers cet enregistrement. Toutefois, si un enregistrement dans un dynaset est supprimé soit par un autre `IsDeleted` utilisateur ou dans un autre jeu d’enregistrements basé sur la même table, retournera TRUE lorsque vous faites défiler plus tard à cet enregistrement.

Pour plus d’informations connexes, consultez les thèmes "Supprimer la méthode", "LastModified Property", et "EditMode Property" dans DAO Help.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a>CDaoRecordset::IsEOF

Appelez cette fonction de membre pendant que vous faites défiler d’enregistrement à enregistrement pour savoir si vous êtes allé au-delà du dernier enregistrement de l’enregistrement.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet ne contient pas d’enregistrements ou si vous avez fait défiler au-delà du dernier enregistrement; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez `IsEOF` également appeler pour déterminer si le jeu d’enregistrement contient des enregistrements ou est vide. Immédiatement après `Open`votre appel, si le `IsEOF` recordet ne contient pas d’enregistrements, renvoie nonzero. Lorsque vous ouvrez un record qui a au moins un `IsEOF` enregistrement, le premier enregistrement est le record actuel et retourne 0.

Si le dernier enregistrement est l’enregistrement actuel lorsque vous appelez, `MoveNext` `IsEOF` retournera par la suite nonzero. Si `IsEOF` les retours nonzero et vous appelez `MoveNext`, une exception est lancée. Si `IsEOF` les déclarations non zéro, le dossier actuel n’est pas défini, et toute action qui nécessite un enregistrement actuel entraînera une exception.

Effet de méthodes `IsBOF` `IsEOF` spécifiques sur et paramètres :

- Appeler `Open` en interne fait le premier enregistrement dans `MoveFirst`le record actuel en appelant . Par conséquent, faire appel `Open` à `IsBOF` `IsEOF` un ensemble vide de causes de records et de retourner nonzero. (Voir le tableau suivant pour `MoveFirst` le comportement d’un appel raté.)

- Toutes les opérations Move qui `IsBOF` réussissent `IsEOF` à localiser un dossier causent à la fois et au retour 0.

- Un `AddNew` appel suivi `Update` d’un appel qui insère avec succès un nouvel enregistrement entraînera le `IsBOF` retour 0, mais seulement si `IsEOF` elle n’est déjà pas zéro. L’état `IsEOF` de volonté restera toujours inchangé. Tel que défini par le moteur de base de données Microsoft Jet, le pointeur d’enregistrement actuel d’un jeu de disques vide est à la fin d’un fichier, de sorte que tout nouvel enregistrement est inséré après l’enregistrement actuel.

- Tout `Delete` appel, même s’il supprime le seul enregistrement restant d’un enregistrement, ne changera pas la valeur de `IsBOF` ou `IsEOF`.

Ce tableau montre quelles opérations De déménagement `IsBOF` /  `IsEOF`sont autorisées avec différentes combinaisons de .

||MoveFirst, MoveLast|MovePrev,<br /><br /> Déplacer < 0|Déplacer 0|Movenext<br /><br /> Déplacer > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`Nonzero,<br /><br /> `IsEOF`=0|Autorisé|Exception|Exception|Autorisé|
|`IsBOF`=0,<br /><br /> `IsEOF`Nonzero|Autorisé|Autorisé|Exception|Exception|
|Les deux nonzero|Exception|Exception|Exception|Exception|
|Les deux 0|Autorisé|Autorisé|Autorisé|Autorisé|

Permettre une opération Move ne signifie pas que l’opération permettra de localiser avec succès un enregistrement. Il indique simplement qu’une tentative d’effectuer l’opération De déménagement spécifiée est autorisée et ne générera pas d’exception. La valeur `IsBOF` des `IsEOF` fonctions et des fonctions des membres peut changer à la suite de la tentative de déménagement.

L’effet des opérations De mouvement qui ne `IsBOF` `IsEOF` trouvent pas d’enregistrement sur la valeur et les paramètres est indiqué dans le tableau suivant.

||IsBOF (isBOF)|IsEOF (IsEOF)|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nonzero (Nonzero)|Nonzero (Nonzero)|
|`Move` 0|Aucun changement|Aucun changement|
|`MovePrev`, `Move` < 0|Nonzero (Nonzero)|Aucun changement|
|`MoveNext`, `Move` > 0|Aucun changement|Nonzero (Nonzero)|

Pour plus d’informations connexes, voir le thème "BOF, EOF Properties" dans DAO Help.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty

Appelez cette fonction de membre pour déterminer si le membre spécifié des données sur le terrain d’un dynaset a été signalé comme « sale » (changé).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Un pointeur pour le membre des données sur le terrain dont vous souhaitez vérifier le statut, ou NULL pour déterminer si l’un des champs sont sales.

### <a name="return-value"></a>Valeur de retour

Nonzero si le membre spécifié des données sur le terrain est signalé comme sale; sinon 0.

### <a name="remarks"></a>Notes

Les données dans tous les membres des données sur le champ sale seront transférées `Update` au dossier `CDaoRecordset` sur la `Edit` source `AddNew`de données lorsque l’enregistrement actuel est mis à jour par un appel à la fonction membre de (suite à un appel à ou à ). Avec ces connaissances, vous pouvez prendre d’autres mesures, telles que le non-inflammage du membre des données sur le terrain pour marquer la colonne afin qu’il ne sera pas écrit à la source de données.

`IsFieldDirty`est mis `DoFieldExchange`en œuvre par .

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>CDaoRecordset::IsFieldNull

Appelez cette fonction de membre pour déterminer si le membre spécifié des données sur le terrain d’un jeu d’enregistrement a été signalé comme null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Un pointeur pour le membre des données sur le terrain dont vous souhaitez vérifier le statut, ou NULL pour déterminer si l’un des champs sont nuls.

### <a name="return-value"></a>Valeur de retour

Nonzero si le membre spécifié des données sur le terrain est signalé comme Null; sinon 0.

### <a name="remarks"></a>Notes

(Dans la terminologie de la base de données, Null signifie « n’avoir aucune valeur » et n’est pas le même que NULL dans C.) Si un membre des données sur le terrain est signalé comme null, il est interprété comme une colonne de l’enregistrement actuel pour lequel il n’y a aucune valeur.

> [!NOTE]
> Dans certaines situations, l’utilisation `IsFieldNull` peut être inefficace, comme l’illustre l’exemple de code suivant :

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> Si vous utilisez la liaison d’enregistrement `CDaoRecordset`dynamique, sans en tirer, assurez-vous d’utiliser VT_NULL comme indiqué dans l’exemple.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable

Appelez cette fonction de membre pour déterminer si le membre spécifié des données sur le terrain est « nul » (peut être réglé à une valeur nulle; LE NULL n’est pas le même que Null, ce qui, selon la terminologie de la base de données, signifie « n’avoir aucune valeur »).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Un pointeur pour le membre des données sur le terrain dont vous souhaitez vérifier le statut, ou NULL pour déterminer si l’un des champs sont nuls.

### <a name="return-value"></a>Valeur de retour

Nonzero si le membre spécifié des données sur le terrain peut être fait Null; sinon 0.

### <a name="remarks"></a>Notes

Un champ qui ne peut pas être Null doit avoir une valeur. Si vous essayez de définir un tel champ à Null lors de l’ajout `Update` ou de la mise à jour d’un enregistrement, la source de données rejette l’ajout ou la mise à jour, et jettera une exception. L’exception se `Update`produit lorsque vous `SetFieldNull`appelez, pas lorsque vous appelez .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a>CDaoRecordset::IsOpen

Appelez cette fonction de membre pour déterminer si le dossier est ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction `Open` de `Requery` l’objet ou du membre de l’enregistrement a déjà été appelée et que le dossier n’a pas été fermé; sinon 0.

### <a name="remarks"></a>Notes

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset::m_bCheckCacheForDirtyFields

Contient un drapeau indiquant si les champs mis en cache sont automatiquement marqués comme sales (changé) et Null.

### <a name="remarks"></a>Notes

Le drapeau par défaut à TRUE. Le paramètre de ce membre des données contrôle l’ensemble du mécanisme de double tampon. Si vous définissez le drapeau en TRUE, vous pouvez désactiver la mise en cache sur une base champ par champ à l’aide du mécanisme DFX. Si vous définissez le drapeau `SetFieldDirty` à `SetFieldNull` FALSE, vous devez appeler et vous-même.

Réglez ce `Open`membre de données avant d’appeler . Ce mécanisme est principalement destiné à la facilité d’utilisation. Les performances peuvent être plus lentes en raison du double tamponnage des champs au fur et à mesure que des changements sont apportés.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a>CDaoRecordset::m_nFields

Contient le nombre de membres des données sur le terrain dans la classe des enregistrements et le nombre de colonnes sélectionnées par le groupe d’enregistrement à partir de la source de données.

### <a name="remarks"></a>Notes

Le constructeur de la classe de `m_nFields` la série d’enregistrements doit être initialisé avec le nombre correct de champs statiquement liés. ClassWizard écrit cette initialisation pour vous lorsque vous l’utilisez pour déclarer votre classe de recordet. Vous pouvez également l’écrire manuellement.

Le cadre utilise ce nombre pour gérer l’interaction entre les membres des données sur le terrain et les colonnes correspondantes de l’enregistrement actuel sur la source de données.

> [!NOTE]
> Ce numéro doit correspondre au nombre `DoFieldExchange` de colonnes `SetFieldType` de `CDaoFieldExchange::outputColumn`sortie enregistrées après un appel avec le paramètre .

Vous pouvez lier les `CDaoRecordset::GetFieldValue` colonnes dynamiquement par le chemin et `CDaoRecordset::SetFieldValue`. Si vous le faites, vous n’avez pas `m_nFields` besoin d’incrémenter le `DoFieldExchange` nombre pour refléter le nombre d’appels de fonction DFX dans votre fonction de membre.

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a>CDaoRecordset::m_nParams

Contient le nombre de paramètres membres dans la classe de l’enregistrement — le nombre de paramètres passés avec la requête du recordet.

### <a name="remarks"></a>Notes

Si votre classe de documents a des membres de données de paramètres, le constructeur de la classe doit initialiser *m_nParams* avec le nombre correct. La valeur de *m_nParams* par défaut à 0. Si vous ajoutez des membres de données de paramètres — ce que vous devez faire manuellement — vous devez également ajouter manuellement une initialisation dans le constructeur de classe pour refléter le nombre de paramètres (qui doivent être au moins aussi grands que le nombre de «» placesholders dans votre *m_strFilter* ou *m_strSort* chaîne).

Le cadre utilise ce nombre lorsqu’il paramélise la requête du recordet.

> [!NOTE]
> Ce numéro doit correspondre au nombre de "params" enregistrés `DoFieldExchange` après un appel avec `SetFieldType` le paramètre `CFieldExchange::param`.

Pour plus d’informations connexes, consultez le thème " Objet paramètre " dans DAO Help.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset

Contient un pointeur à l’interface OLE pour `CDaoRecordset` l’objet DAO recordet sous-jacent à l’objet.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous avez besoin d’accéder à l’interface DAO directement.

Pour plus d’informations connexes, consultez le sujet "Objet Recordet" dans DAO Help.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase

Contient un pointeur sur l’objet `CDaoDatabase` par lequel le jeu d’enregistrement est connecté à une source de données.

### <a name="remarks"></a>Notes

Cette variable est définie de deux façons. En règle générale, vous passez `CDaoDatabase` un pointeur à un objet déjà ouvert lorsque vous construisez l’objet de l’enregistrement. Si vous passez NULL `CDaoRecordset` à `CDaoDatabase` la place, crée un objet pour vous et l’ouvre. Dans les `CDaoRecordset` deux cas, stocke le pointeur dans cette variable.

Normalement, vous n’aurez pas directement `m_pDatabase`besoin d’utiliser le pointeur stocké dans . Si vous écrivez vos `CDaoRecordset`propres extensions à , cependant, vous pourriez avoir besoin d’utiliser le pointeur. Par exemple, vous pourriez avoir besoin `CDaoException`du pointeur si vous lancez votre propre (s).

Pour obtenir des informations connexes, consultez le thème « Objet de base de données » dans DAO Help.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a>CDaoRecordset::m_strFilter

Contient une chaîne qui est utilisée pour construire la clause **WHERE** d’une déclaration SQL.

### <a name="remarks"></a>Notes

Il n’inclut pas le mot réservé **Où** filtrer l’ensemble d’enregistrements. L’utilisation de ce membre des données ne s’applique pas aux ensembles de documents de type table. L’utilisation `m_strFilter` de n’a aucun effet `CDaoQueryDef` lors de l’ouverture d’un enregistrement à l’aide d’un pointeur.

Utilisez le format de date des États-Unis (année de jour) lorsque vous filtrez les champs contenant des dates, même si vous n’utilisez pas la version américaine du moteur de base de données Microsoft Jet; autrement, les données peuvent ne pas être filtrées comme vous vous y attendez.

Pour obtenir des informations connexes, consultez le thème « Propriété de filtre » dans DAO Help.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a>CDaoRecordset::m_strSort

Contient une chaîne contenant la clause **ORDERBY** d’une déclaration SQL sans les mots réservés **ORDERBY**.

### <a name="remarks"></a>Notes

Vous pouvez trier les objets de type dynaset et instantané.

Vous ne pouvez pas trier les objets de type de table. Pour déterminer le tri d’ordre d’un jeu d’enregistrement de type table, appelez [SetCurrentIndex](#setcurrentindex).

L’utilisation de *m_strSort* n’a aucun effet lors `CDaoQueryDef` de l’ouverture d’un recordet à l’aide d’un pointeur.

Pour obtenir des informations connexes, consultez le thème « Tri Property » dans DAO Help.

## <a name="cdaorecordsetmove"></a><a name="move"></a>CDaoRecordset::Déplacer

Appelez cette fonction de membre pour positionner les enregistrements *lRows* de l’enregistrement actuel.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Paramètres

*lRows (en)*<br/>
Le nombre d’enregistrements pour aller de l’avant ou vers l’arrière. Les valeurs positives avancent, vers la fin de l’enregistrement. Les valeurs négatives reculent, vers le début.

### <a name="remarks"></a>Notes

Vous pouvez aller de l’avant ou vers l’arrière. `Move( 1 )`est équivalent `MoveNext`à `Move( -1 )` , `MovePrev`et est équivalent à .

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. En général, `IsBOF` appelez `IsEOF` à la fois et avant une opération Move pour déterminer si le dossier a des dossiers. Après avoir `Open` `Requery`appelé ou `IsBOF` `IsEOF`, appelez l’un ou l’autre ou .

> [!NOTE]
> Si vous avez fait défiler au-delà `IsBOF` du `IsEOF` début ou de la `Move` fin `CDaoException`du recordet (ou retourne nonzero), un appel pour jeter un .

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Lorsque vous `Move` faites appel à un instantané défilement avant seulement, le paramètre *lRows* doit être un intégrier positif et les signets ne sont pas autorisés, de sorte que vous pouvez aller de l’avant seulement.

Pour faire le premier, dernier, prochain, ou précédent enregistrement dans `MoveFirst` `MoveLast`un `MoveNext`enregistrement `MovePrev` d’enregistrement, appelez le , , , ou la fonction de membre.

Pour plus d’informations connexes, consultez les thèmes «Move Method» et «MoveFirst, MoveLast, MoveNext, MovePrevious Methods» dans DAO Help.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a>CDaoRecordset::MoveFirst

Appelez cette fonction de membre pour faire le premier enregistrement dans le dossier (le cas échéant) le dossier actuel.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Notes

Vous n’avez `MoveFirst` pas à appeler immédiatement après avoir ouvert le dossier. À ce moment-là, le premier enregistrement (le cas échéant) est automatiquement l’enregistrement actuel.

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. En général, `IsBOF` appelez `IsEOF` à la fois et avant une opération Move pour déterminer si le dossier a des dossiers. Après avoir `Open` `Requery`appelé ou `IsBOF` `IsEOF`, appelez l’un ou l’autre ou .

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Utilisez `Move` les fonctions pour passer de l’enregistrement à l’enregistrement sans appliquer de condition. Utilisez les opérations Trouver pour localiser les enregistrements dans un objet de type album de type dynaset ou instantané qui satisfont à une certaine condition. Pour localiser un enregistrement dans un objet `Seek`de type de tableau, appelez .

Si le jeu d’enregistrement fait référence à un jeu d’enregistrement de type table, le mouvement suit l’indice actuel du tableau. Vous pouvez définir l’indice actuel en utilisant la propriété Index de l’objet DAO sous-jacent. Si vous ne définissez pas l’indice actuel, l’ordre des enregistrements retournés n’est pas défini.

Si vous `MoveLast` faites appel à un objet de recordet basé sur une requête SQL ou une requête, la requête est forcée de se terminer et l’objet de la liste des enregistrements est entièrement peuplé.

Vous ne `MoveFirst` pouvez `MovePrev` pas appeler la fonction ou le membre avec un instantané de défilement avant seulement.

Pour déplacer la position de l’enregistrement actuel dans un objet de `Move`registre un nombre spécifique d’enregistrements vers l’avant ou vers l’arrière, appelez .

Pour plus d’informations connexes, consultez les thèmes «Move Method» et «MoveFirst, MoveLast, MoveNext, MovePrevious Methods» dans DAO Help.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a>CDaoRecordset::MoveLast

Appelez cette fonction de membre pour faire le dernier enregistrement (le cas échéant) dans le dossier d’enregistrement actuel.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Notes

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. En général, `IsBOF` appelez `IsEOF` à la fois et avant une opération Move pour déterminer si le dossier a des dossiers. Après avoir `Open` `Requery`appelé ou `IsBOF` `IsEOF`, appelez l’un ou l’autre ou .

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Utilisez `Move` les fonctions pour passer de l’enregistrement à l’enregistrement sans appliquer de condition. Utilisez les opérations Trouver pour localiser les enregistrements dans un objet de type album de type dynaset ou instantané qui satisfont à une certaine condition. Pour localiser un enregistrement dans un objet `Seek`de type de tableau, appelez .

Si le jeu d’enregistrement fait référence à un jeu d’enregistrement de type table, le mouvement suit l’indice actuel du tableau. Vous pouvez définir l’indice actuel en utilisant la propriété Index de l’objet DAO sous-jacent. Si vous ne définissez pas l’indice actuel, l’ordre des enregistrements retournés n’est pas défini.

Si vous `MoveLast` faites appel à un objet de recordet basé sur une requête SQL ou une requête, la requête est forcée de se terminer et l’objet de la liste des enregistrements est entièrement peuplé.

Pour déplacer la position de l’enregistrement actuel dans un objet de `Move`registre un nombre spécifique d’enregistrements vers l’avant ou vers l’arrière, appelez .

Pour plus d’informations connexes, consultez les thèmes «Move Method» et «MoveFirst, MoveLast, MoveNext, MovePrevious Methods» dans DAO Help.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a>CDaoRecordset::MoveNext

Appelez cette fonction de membre pour faire le prochain enregistrement dans le dossier d’enregistrement actuel.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Notes

Il est recommandé `IsBOF` d’appeler avant de tenter de passer à l’enregistrement précédent. Un appel `MovePrev` à `CDaoException` lancer `IsBOF` un si renvoie nonzero, indiquant soit que vous avez déjà fait défiler avant le premier enregistrement ou qu’aucun enregistrement n’a été sélectionné par le recordet.

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. En général, `IsBOF` appelez `IsEOF` à la fois et avant une opération Move pour déterminer si le dossier a des dossiers. Après avoir `Open` `Requery`appelé ou `IsBOF` `IsEOF`, appelez l’un ou l’autre ou .

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Utilisez `Move` les fonctions pour passer de l’enregistrement à l’enregistrement sans appliquer de condition. Utilisez les opérations Trouver pour localiser les enregistrements dans un objet de type album de type dynaset ou instantané qui satisfont à une certaine condition. Pour localiser un enregistrement dans un objet `Seek`de type de tableau, appelez .

Si le jeu d’enregistrement fait référence à un jeu d’enregistrement de type table, le mouvement suit l’indice actuel du tableau. Vous pouvez définir l’indice actuel en utilisant la propriété Index de l’objet DAO sous-jacent. Si vous ne définissez pas l’indice actuel, l’ordre des enregistrements retournés n’est pas défini.

Pour déplacer la position de l’enregistrement actuel dans un objet de `Move`registre un nombre spécifique d’enregistrements vers l’avant ou vers l’arrière, appelez .

Pour plus d’informations connexes, consultez les thèmes «Move Method» et «MoveFirst, MoveLast, MoveNext, MovePrevious Methods» dans DAO Help.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a>CDaoRecordset::MovePrev

Appelez cette fonction de membre pour faire l’enregistrement précédent dans le dossier d’enregistrement actuel.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Notes

Il est recommandé `IsBOF` d’appeler avant de tenter de passer à l’enregistrement précédent. Un appel `MovePrev` à `CDaoException` lancer `IsBOF` un si renvoie nonzero, indiquant soit que vous avez déjà fait défiler avant le premier enregistrement ou qu’aucun enregistrement n’a été sélectionné par le recordet.

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. En général, `IsBOF` appelez `IsEOF` à la fois et avant une opération Move pour déterminer si le dossier a des dossiers. Après avoir `Open` `Requery`appelé ou `IsBOF` `IsEOF`, appelez l’un ou l’autre ou .

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Utilisez `Move` les fonctions pour passer de l’enregistrement à l’enregistrement sans appliquer de condition. Utilisez les opérations Trouver pour localiser les enregistrements dans un objet de type album de type dynaset ou instantané qui satisfont à une certaine condition. Pour localiser un enregistrement dans un objet `Seek`de type de tableau, appelez .

Si le jeu d’enregistrement fait référence à un jeu d’enregistrement de type table, le mouvement suit l’indice actuel du tableau. Vous pouvez définir l’indice actuel en utilisant la propriété Index de l’objet DAO sous-jacent. Si vous ne définissez pas l’indice actuel, l’ordre des enregistrements retournés n’est pas défini.

Vous ne `MoveFirst` pouvez `MovePrev` pas appeler la fonction ou le membre avec un instantané de défilement avant seulement.

Pour déplacer la position de l’enregistrement actuel dans un objet de `Move`registre un nombre spécifique d’enregistrements vers l’avant ou vers l’arrière, appelez .

Pour plus d’informations connexes, consultez les thèmes «Move Method» et «MoveFirst, MoveLast, MoveNext, MovePrevious Methods» dans DAO Help.

## <a name="cdaorecordsetopen"></a><a name="open"></a>CDaoRecordset::Ouvert

Vous devez appeler cette fonction de membre pour récupérer les enregistrements de l’enregistrement.

```
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>Paramètres

*nOpenType (en)*<br/>
L’une des valeurs suivantes :

- `dbOpenDynaset`Un jeu dynaset de type avec défilement bidirectionnel. Il s’agit de la valeur par défaut.

- `dbOpenTable`Un jeu d’enregistrement de type table avec défilement bidirectionnel.

- `dbOpenSnapshot`Un enregistrement de type instantané avec défilement bidirectionnel.

*lpszSQL*<br/>
Un pointeur de chaîne contenant l’un des éléments suivants :

- Un pointeur NULL.

- Le nom d’un ou plusieurs dépôts et/ou requêtes (séparés par virgule).

- Une déclaration SQL **SELECT** (optionnelle avec une clause SQL **WHERE** ou **ORDERBY).**

- Une requête de passage.

*nOptions*<br/>
Une ou plusieurs des options énumérées ci-dessous. La valeur par défaut est 0. Les valeurs possibles sont les suivantes :

- `dbAppendOnly`Vous ne pouvez ajouter que de nouveaux enregistrements (enregistrement de type dynaset uniquement). Cette option signifie littéralement que les enregistrements ne peuvent être annexés. Les classes de base de données MFC ODBC disposent d’une option annexe uniquement qui permet de récupérer et d’apprener les enregistrements.

- `dbForwardOnly`Le livrement est un instantané de défilement avant seulement.

- `dbSeeChanges`Générez une exception si un autre utilisateur modifie les données que vous modifiez.

- `dbDenyWrite`D’autres utilisateurs ne peuvent pas modifier ou ajouter des enregistrements.

- `dbDenyRead`D’autres utilisateurs ne peuvent pas afficher les enregistrements (tableau de type enregistrements seulement).

- `dbReadOnly`Vous ne pouvez afficher que les enregistrements; d’autres utilisateurs peuvent les modifier.

- `dbInconsistent`Des mises à jour incohérentes sont autorisées (enregistrement de type dynaset uniquement).

- `dbConsistent`Seules des mises à jour cohérentes sont autorisées (enregistrement de type dynaset uniquement).

> [!NOTE]
> Les `dbConsistent` constantes `dbInconsistent` et s’excluent mutuellement. Vous pouvez utiliser l’un ou l’autre, `Open`mais pas les deux dans un cas donné de .

*pTableDef*<br/>
Un pointeur sur un objet [CDaoTableDef.](../../mfc/reference/cdaotabledef-class.md) Cette version n’est valable que pour les enregistrements de type table. Lors de l’utilisation de cette option, le `CDaoDatabase` pointeur utilisé pour construire le n’est `CDaoRecordset` pas utilisé; au contraire, la base de données dans laquelle réside le dépôt est utilisée.

*pQueryDef*<br/>
Un pointeur à un objet [CDaoQueryDef.](../../mfc/reference/cdaoquerydef-class.md) Cette version n’est valable que pour les enregistrements de type dynaset et instantané. Lors de l’utilisation de cette option, le `CDaoDatabase` pointeur utilisé pour construire le n’est `CDaoRecordset` pas utilisé; au contraire, la base de données dans laquelle réside la requête est utilisée.

### <a name="remarks"></a>Notes

Avant `Open`d’appeler, vous devez construire l’objet de l’enregistrement. Pour ce faire, plusieurs méthodes sont possibles :

- Lorsque vous construisez l’objet de l’enregistrement, passez un pointeur sur un `CDaoDatabase` objet déjà ouvert.

- Lorsque vous construisez l’objet de l’enregistrement, passez un pointeur à un `CDaoDatabase` objet qui n’est pas ouvert. Le recordet `CDaoDatabase` ouvre un objet, mais ne le fermera pas lorsque l’objet de l’enregistrement se ferme.

- Lorsque vous construisez l’objet de l’enregistrement, passez un pointeur NULL. L’objet de `GetDefaultDBName` l’enregistrement appelle pour obtenir le nom de l’accès Microsoft . Fichier MDB à ouvrir. Le recordet ouvre `CDaoDatabase` alors un objet et le garde ouvert tant que le recordet est ouvert. Lorsque vous `Close` appelez sur l’ensemble d’enregistrements, l’objet `CDaoDatabase` est également fermé.

    > [!NOTE]
    >  Lorsque le recordet `CDaoDatabase` ouvre l’objet, il ouvre la source de données avec un accès non exclusif.

Pour la `Open` version de cela utilise le paramètre *lpszSQL,* une fois que le livre d’enregistrement est ouvert, vous pouvez récupérer des enregistrements de l’une des plusieurs façons. La première option est d’avoir des `DoFieldExchange`fonctions DFX dans votre . La deuxième option consiste à utiliser `GetFieldValue` la liaison dynamique en appelant la fonction membre. Ces options peuvent être mises en œuvre séparément ou en combinaison. S’ils sont combinés, vous devrez passer dans la déclaration `Open`SQL vous-même sur l’appel à .

Lorsque vous utilisez la `Open` deuxième version de `CDaoTableDef` l’endroit où vous passez dans `DoFieldExchange` un objet, les colonnes résultantes `GetFieldValue`seront disponibles pour vous lier via et le mécanisme DFX, et / ou se lier dynamiquement via .

> [!NOTE]
> Vous ne `Open` pouvez `CDaoTableDef` appeler qu’à l’aide d’un objet pour des enregistrements de type table.

Lorsque vous utilisez la `Open` troisième version de `CDaoQueryDef` l’endroit où vous passez dans un objet, cette requête `DoFieldExchange` sera exécutée, et les colonnes `GetFieldValue`résultantes seront disponibles pour vous de lier via et le mécanisme DFX, et / ou lier dynamiquement via .

> [!NOTE]
> Vous ne `Open` pouvez `CDaoQueryDef` appeler qu’à l’aide d’un objet pour des enregistrements de type dynaset et instantanés.

Pour la première `Open` version `lpszSQL` de ce qui utilise le paramètre, les enregistrements sont sélectionnés en fonction des critères indiqués dans le tableau suivant.

|Valeur du paramètre `lpszSQL`.|Les enregistrements sélectionnés sont déterminés par|Exemple|
|--------------------------------------|----------------------------------------|-------------|
|NULL|La chaîne `GetDefaultSQL`est revenue par .||
|Une liste séparée par virgule d’un ou plusieurs noms de dépôt et/ou de requête.|Toutes les colonnes `DoFieldExchange`représentées dans le .|`"Customer"`|
|**LISTE** DE colonne SELECT **FROM** table-list|Les colonnes spécifiées à partir du tableau spécifié et/ou de la requête(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

La procédure habituelle consiste à `Open`passer NULL à ; dans ce `Open` cas, les appels `GetDefaultSQL`, une fonction de membre `CDaoRecordset`primordiale que ClassWizard génère lors de la création d’une classe dérivée. Cette valeur donne le nom de tabledef et/ou de requête querydef que vous avez spécifié dans ClassWizard. Vous pouvez plutôt spécifier d’autres informations dans le paramètre *lpszSQL.*

Quoi que vous `Open` passiez, construit une chaîne SQL finale pour la requête (la chaîne peut avoir SQL **WHERE** et **ORDERBY** clauses annexées à la chaîne *lpszSQL* que vous avez passé) et exécute ensuite la requête. Vous pouvez examiner la `GetSQL` chaîne `Open`construite en appelant après avoir appelé .

Les membres des données de terrain de votre classe de documents sont liés aux colonnes des données sélectionnées. Si des enregistrements sont retournés, le premier enregistrement devient le record actuel.

Si vous souhaitez définir des options pour le jeu d’enregistrement, comme un filtre ou une sorte, défini `m_strSort` ou `m_strFilter` après avoir construit l’objet de l’enregistrement, mais avant d’appeler `Open`. Si vous souhaitez rafraîchir les enregistrements dans le dossier après `Requery`que le recordet est déjà ouvert, appelez .

Si vous `Open` faites appel à un jeu d’enregistrement de type dynaset ou instantané, ou si la source de données `dbOpenTable` fait référence à une déclaration SQL ou à un dépôt qui représente une table jointe, vous ne pouvez pas utiliser pour l’argument de type; si vous le faites, MFC lance une exception. Pour déterminer si un objet de dépôt représente une table jointe, créez un objet [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) et appelez sa fonction de membre [GetConnect.](../../mfc/reference/cdaotabledef-class.md#getconnect)

Utilisez `dbSeeChanges` le drapeau si vous souhaitez piéger les modifications apportées par un autre utilisateur ou un autre programme sur votre machine lorsque vous modifiez ou supprimerez le même enregistrement. Par exemple, si deux utilisateurs commencent à modifier le `Update` même enregistrement, le premier utilisateur à appeler la fonction membre réussit. Quand `Update` est appelé par le `CDaoException` deuxième utilisateur, un est jeté. De même, si le `Delete` deuxième utilisateur tente d’appeler pour supprimer l’enregistrement, et il a déjà été modifié par le premier utilisateur, un `CDaoException` se produit.

En règle générale, `CDaoException` si l’utilisateur obtient cela lors de la mise à jour, votre code doit actualiser le contenu des champs et récupérer les valeurs nouvellement modifiées. Si l’exception se produit dans le processus de suppression, votre code peut afficher les nouvelles données d’enregistrement à l’utilisateur et un message indiquant que les données ont récemment changé. À ce stade, votre code peut demander une confirmation que l’utilisateur veut toujours supprimer l’enregistrement.

> [!TIP]
> Utilisez l’option de défilement vers l’avant seulement (`dbForwardOnly`) pour améliorer les performances lorsque votre application effectue une seule passe à travers un jeu d’enregistrement ouvert à partir d’une source de données ODBC.

Pour plus d’informations connexes, voir le thème "OpenRecordset Method" dans DAO Help.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a>CDaoRecordset::Requery

Appelez cette fonction de membre pour reconstruire (rafraîchir) un dossier.

```
virtual void Requery();
```

### <a name="remarks"></a>Notes

Si des enregistrements sont retournés, le premier enregistrement devient le record actuel.

Afin que le carnet de données reflète les ajouts et les suppressions que vous ou d’autres `Requery`utilisateurs faites à la source de données, vous devez reconstruire le jeu d’enregistrement en appelant . Si le jeu d’enregistrement est un dynaset, il reflète automatiquement les mises à jour que vous ou d’autres utilisateurs faites à ses enregistrements existants (mais pas des ajouts). Si le livre est un instantané, vous devez appeler `Requery` pour refléter les modifications par d’autres utilisateurs ainsi que les ajouts et les suppressions.

Pour un dynaset ou un `Requery` instantané, appelez chaque fois que vous voulez reconstruire le jeu d’enregistrement en utilisant des valeurs de paramètres. Réglez le nouveau filtre ou tri en définissez `Requery` [m_strFilter](#m_strfilter) et [m_strSort](#m_strsort) avant d’appeler . Définissez de nouveaux paramètres en affectant de `Requery`nouvelles valeurs aux membres des données de paramètre avant d’appeler .

Si la tentative de reconstruction du recordet échoue, le recordet est fermé. Avant d’appeler, `Requery`vous pouvez déterminer si le dossier peut être requeried en appelant la fonction membre [CanRestart.](#canrestart) `CanRestart`ne garantit `Requery` pas que cela réussira.

> [!CAUTION]
> Appelez `Requery` seulement après `Open`que vous avez appelé .

> [!NOTE]
> Appeler [Requery](#requery) change les signets DAO.

Vous ne pouvez `Requery` pas faire appel à un jeu d’enregistrement `CanRestart` de type dynaset ou instantané si vous appelez les retours 0, ni vous ne pouvez l’utiliser sur un jeu d’enregistrement de type table.

Si `IsBOF` les `IsEOF` deux et retourner `Requery`nonzero après que vous appelez , la requête n’a pas retourné d’enregistrements et le recordet ne contiendra aucune donnée.

Pour plus d’informations connexes, voir le thème "Méthode requery" dans DAO Aide.

## <a name="cdaorecordsetseek"></a><a name="seek"></a>CDaoRecordset::Chercher

Appelez cette fonction de membre pour localiser l’enregistrement dans un objet indexé de type de tableau qui satisfait les critères spécifiés pour l’index actuel et faire de cet enregistrement le dossier actuel.

```
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>Paramètres

*lpszComparison*<br/>
L’une des expressions de chaîne suivantes\<: « < », « « », « » « >» ou « > ».

*pKey1*<br/>
Un pointeur à un [COleVariant](../../mfc/reference/colevariant-class.md) dont la valeur correspond au premier champ de l’indice. Obligatoire.

*pKey2 (en)*<br/>
Un pointeur `COleVariant` à un dont la valeur correspond au deuxième champ de l’indice, le cas échéant. Défauts à NULL.

*pKey3 (en)*<br/>
Un pointeur `COleVariant` à un dont la valeur correspond au troisième champ de l’indice, le cas échéant. Défauts à NULL.

*pKeyArray (en)*<br/>
Un pointeur à un tableau de variantes. La taille du tableau correspond au nombre de champs dans l’index.

*nKeys (en)*<br/>
Un intégrant correspondant à la taille du tableau, qui est le nombre de champs dans l’index.

> [!NOTE]
> Ne spécifiez pas les wildcards dans les touches. Wildcards ne `Seek` fera pas retourner les enregistrements correspondants.

### <a name="return-value"></a>Valeur de retour

Nonzero si des enregistrements correspondants sont trouvés, sinon 0.

### <a name="remarks"></a>Notes

Utilisez la deuxième version `Seek` (de tableau) pour gérer les index de quatre champs ou plus.

`Seek`permet la recherche d’index haute performance sur les ensembles de dossiers de type table. Vous devez définir l’indice `Seek`actuel en appelant avant d’appeler `SetCurrentIndex` . Si l’index identifie un champ clé `Seek` non unique ou des champs, localise le premier enregistrement qui répond aux critères. Si vous ne définissez pas un index, une exception est lancée.

Notez que si vous ne créez pas `COleVariant` un carnet UNICODE, les objets doivent être explicitement déclarés ANSI. Cela peut être fait en utilisant le [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* `VT_BSTRT` **)** forme de constructeur `COleVariant` avec *vtSrc* mis à (ANSI) ou en utilisant la `VT_BSTRT`fonction [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** avec *vtSrc* réglé à .

Lorsque vous `Seek`appelez, vous passez une ou plusieurs valeurs clés et un\<opérateur de comparaison ("<", "' ' ' ' ' ' ' ' ' ' ' ' ' ' ' >' ' ' > ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' `Seek`recherche à travers les champs clés spécifiés et localise le premier enregistrement qui répond aux critères spécifiés par *lpszComparison* et *pKey1*. Une fois `Seek` trouvé, retourne nonzero, et rend cet enregistrement actuel. Si `Seek` vous ne paruz pas sur un match, `Seek` retourne zéro, et le record actuel n’est pas défini. Lorsque vous utilisez DAO directement, vous devez vérifier explicitement la propriété NoMatch.

S’il `lpszComparison` s’agit de «md», de « >`Seek` » ou de « > », commence au début de l’indice. Si *lpszComparison* est "<" ou "<", `Seek` commence à la fin de l’index et recherche vers l’arrière à moins qu’il n’y ait des entrées d’index en double à la fin. Dans ce `Seek` cas, commence à une entrée arbitraire parmi les entrées de l’indice en double à la fin de l’indice.

Il n’est pas doit y `Seek`avoir un enregistrement actuel lorsque vous utilisez .

Pour localiser un enregistrement dans un ensemble d’enregistrements de type dynaset ou instantané qui satisfait une condition spécifique, utilisez les opérations Trouver. Pour inclure tous les enregistrements, et pas seulement ceux qui satisfont à une condition spécifique, utilisez les opérations Move pour passer d’un enregistrement à l’autre.

Vous ne `Seek` pouvez pas faire appel à une table jointe de tout type parce que les tables ci-jointes doivent être ouvertes sous forme d’enregistrements de type dynaset ou instantané. Toutefois, si `CDaoDatabase::Open` vous appelez pour ouvrir directement une base `Seek` de données ISAM installable, vous pouvez faire appel à des tables dans cette base de données, bien que les performances puissent être lentes.

Pour obtenir des informations connexes, consultez le thème « Rechercher la méthode » dans DAO Help.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CDaoRecordset::SetAbsolutePosition

Établit le nombre record relatif de l’enregistrement actuel d’un objet de recordet.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Paramètres

*lPosition*<br/>
Correspond à la position ordinaire du dossier actuel dans le dossier.

### <a name="remarks"></a>Notes

L’appel `SetAbsolutePosition` vous permet de positionner le pointeur d’enregistrement actuel à un enregistrement spécifique en fonction de sa position ordinaire dans un jeu d’enregistrement de type dynaset ou instantané. Vous pouvez également déterminer le nombre record actuel en appelant [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
> Cette fonction de membre n’est valable que pour les enregistrements de type dynaset et instantanés.

La valeur de propriété AbsolutePosition de l’objet DAO sous-jacent est basée à zéro; un réglage de 0 se réfère au premier enregistrement dans le record. L’établissement d’une valeur supérieure au nombre d’enregistrements peuplés amène MFC à jeter une exception. Vous pouvez déterminer le nombre d’enregistrements peuplés `GetRecordCount` dans l’enregistrement en appelant la fonction membre.

Si l’enregistrement actuel est supprimé, la valeur de la propriété AbsolutePosition n’est pas définie, et MFC lance une exception si elle est référencée. De nouveaux enregistrements sont ajoutés à la fin de la séquence.

> [!NOTE]
> Cette propriété n’est pas destinée à être utilisée comme un numéro de dossier de substitution. Les signets sont toujours le moyen recommandé de conserver et de revenir à une position donnée et sont le seul moyen de positionner le record actuel à travers tous les types d’objets de carnet qui prennent en charge les signets. En particulier, la position d’un enregistrement donné change lorsque l’enregistrement(s) qui le précède est supprimé. Rien ne garantit non plus qu’un dossier donné aura la même position absolue si le dossier est recréé à nouveau parce que l’ordre des enregistrements individuels dans un dossier n’est pas garanti à moins qu’il ne soit créé avec une déclaration SQL à l’aide d’une clause **ORDERBY.**

Pour obtenir des informations connexes, consultez le thème « AbsolutePosition Property » dans DAO Help.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>CDaoRecordset::SetBookmark

Appelez cette fonction de membre pour positionner l’enregistrement sur l’enregistrement contenant le signet spécifié.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Paramètres

*varBookmark (en)*<br/>
Un objet [COleVariant](../../mfc/reference/colevariant-class.md) contenant la valeur du signet pour un enregistrement spécifique.

### <a name="remarks"></a>Notes

Lorsqu’un objet de collection est créé ou ouvert, chacun de ses disques a déjà un signet unique. Vous pouvez récupérer le signet de `GetBookmark` l’enregistrement en `COleVariant` cours en appelant et en économisant la valeur d’un objet. Vous pouvez plus tard revenir `SetBookmark` à cet enregistrement en appelant en utilisant la valeur de signet enregistré.

> [!NOTE]
> Appeler [Requery](#requery) change les signets DAO.

Notez que si vous ne créez pas `COleVariant` un ensemble d’enregistrements UNICODE, l’objet doit être explicitement déclaré ANSI. Cela peut être fait en utilisant le [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* `VT_BSTRT` **)** forme de constructeur `COleVariant` avec *vtSrc* mis à (ANSI) ou en utilisant la `VT_BSTRT`fonction [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** avec *vtSrc* réglé à .

Pour plus d’informations connexes, consultez les thèmes «Bookmark Property» et Signmarkable Property dans DAO Help.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>CDaoRecordset::SetCacheSize

Appelez cette fonction de membre pour définir le nombre d’enregistrements à mettre en cache.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Paramètres

*lSize*<br/>
Précise le nombre d’enregistrements. Une valeur typique est de 100. Un réglage de 0 éteint la mise en cache. Le réglage doit être entre 5 et 1200 enregistrements. Le cache peut utiliser une quantité considérable de mémoire.

### <a name="remarks"></a>Notes

Un cache est un espace de mémoire locale qui détient les données les plus récemment récupérées sur le serveur dans le cas où les données seront demandées à nouveau pendant que l’application est en cours d’exécution. La mise en cache de données améliore les performances d’une application qui récupère les données d’un serveur distant grâce à des objets de type album de type dynaset. Lorsque des données sont demandées, le moteur de base de données Microsoft Jet vérifie d’abord le cache pour les données demandées plutôt que de les récupérer à partir du serveur, ce qui prend plus de temps. Les données qui ne proviennent pas d’une source de données ODBC ne sont pas enregistrées dans le cache.

Toute source de données ODBC, telle qu’une table jointe, peut avoir un cache local. Pour créer le cache, ouvrez un objet de `SetCacheSize` l’ensemble d’enregistrements à partir de la source de données à distance, appelez les fonctions et `SetCacheStart` les fonctions du membre, puis appelez la `FillCache` fonction du membre ou passez les enregistrements en utilisant l’une des opérations Move. Le paramètre *lSize* de la `SetCacheSize` fonction membre peut être basé sur le nombre d’enregistrements avec lesquels votre demande peut fonctionner en même temps. Par exemple, si vous utilisez un jeu d’enregistrement comme source des données `SetCacheSize` à afficher à l’écran, vous pouvez passer le *paramètre lSize* comme 20 pour afficher 20 enregistrements en même temps.

Pour plus d’informations connexes, consultez le thème "CacheSize, CacheStart Properties" dans DAO Help.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>CDaoRecordset::SetCacheStart

Appelez cette fonction de membre pour spécifier le signet du premier enregistrement dans le livre d’enregistrement à mettre en cache.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Paramètres

*varBookmark (en)*<br/>
Un [COleVariant](../../mfc/reference/colevariant-class.md) qui spécifie le signet du premier enregistrement dans le livre à être mis en cache.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la valeur de signet de n’importe quel enregistrement pour le paramètre *varBookmark* de la `SetCacheStart` fonction membre. Faites l’enregistrement que vous souhaitez démarrer le cache avec l’enregistrement actuel, établir un signet pour cet `SetCacheStart` enregistrement en utilisant [SetBookmark](#setbookmark), et passer la valeur de signet comme paramètre pour la fonction membre.

Le moteur de base de données Microsoft Jet demande des enregistrements dans la gamme de caches à partir du cache, et il demande des enregistrements en dehors de la gamme de cache du serveur.

Les enregistrements récupérés dans le cache ne reflètent pas les modifications apportées simultanément aux données source par d’autres utilisateurs.

Pour forcer une mise à jour de toutes les données `SetCacheSize` mises en `SetCacheSize` cache, passez le paramètre *lSize* de `FillCache` 0, appelez à nouveau avec la taille du cache que vous avez demandé à l’origine, puis appelez la fonction membre.

Notez que si vous ne créez pas `COleVariant` un ensemble d’enregistrements UNICODE, l’objet doit être explicitement déclaré ANSI. Cela peut être fait en utilisant le [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* `VT_BSTRT` **)** forme de constructeur `COleVariant` avec *vtSrc* mis à (ANSI) ou en utilisant la `VT_BSTRT`fonction [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** avec *vtSrc* réglé à .

Pour plus d’informations connexes, consultez le sujet CacheSize, CacheStart Properties" dans DAO Help.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>CDaoRecordset::SetCurrentIndex

Appelez cette fonction de membre pour définir un index sur un ensemble de records de type table.

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
Un pointeur contenant le nom de l’index à définir.

### <a name="remarks"></a>Notes

Les enregistrements dans les tables de base ne sont pas stockés dans un ordre particulier. La fixation d’un index modifie l’ordre des enregistrements retournés de la base de données, mais il n’affecte pas l’ordre dans lequel les enregistrements sont stockés. L’indice spécifié doit déjà être défini. Si vous essayez d’utiliser un objet index qui n’existe pas, ou si l’index n’est pas défini lorsque vous appelez [Seek](#seek), MFC lance une exception.

Vous pouvez créer un nouvel indice pour le tableau en appelant [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) et appending le nouvel index à la collection Indexes du dépôt sous-jacent en appelant [CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append), puis la réouverture de la collection de disques.

Les enregistrements retournés à partir d’un tableau de type enregistrements ne peuvent être commandés que par les index définis pour le dépôt sous-jacent. Pour trier les enregistrements dans une autre commande, vous pouvez ouvrir un ensemble d’enregistrements de type dynaset ou instantané à l’aide d’une clause **ORDERBY** SQL stockée dans [CDaoRecordset::m_strSort](#m_strsort).

Pour obtenir des informations connexes, consultez le thème « Objet indiciel » et la définition « indice actuel » dans DAO Help.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>CDaoRecordset::SetFieldDirty

Appelez cette fonction de membre pour signaler un membre des données sur le terrain de l’enregistrement comme changé ou comme inchangé.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Contient l’adresse d’un membre des données sur le terrain dans l’enregistrement ou NULL. Si NULL, tous les membres des données sur le terrain dans le jeu d’enregistrement sont signalés. (C-NULL n’est pas le même que Null dans la terminologie de base de données, ce qui signifie « n’avoir aucune valeur. »)

*bDirty (en)*<br/>
VRAI si le membre des données sur le terrain doit être signalé comme «sale» (changé). Autrement FALSE si le membre des données sur le terrain doit être signalé comme «propre» (inchangé).

### <a name="remarks"></a>Notes

Le marquage des champs comme inchangés assure que le champ n’est pas mis à jour.

Le cadre marque les données modifiées des membres des données sur le terrain pour s’assurer qu’ils seront écrits au dossier sur la source de données par le mécanisme d’échange de champs de disques DAO (DFX). Changer la valeur d’un champ définit généralement le champ `SetFieldDirty` sale automatiquement, de sorte que vous aurez rarement besoin de vous appeler, mais vous voudrez peut-être parfois s’assurer que les colonnes seront explicitement mis à jour ou insérés quelle que soit la valeur dans le membre des données de champ. Le mécanisme DFX utilise également PSEUDONULL. Pour plus d’informations, voir [CDaoFieldExchange:m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Si le mécanisme de double tampon n’est pas utilisé, alors changer la valeur du champ ne met pas automatiquement le champ comme sale. Dans ce cas, il sera nécessaire de définir explicitement le champ comme sale. Le drapeau contenu dans [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) contrôle cette vérification automatique sur le terrain.

> [!NOTE]
> Appelez cette fonction de membre seulement après que vous avez appelé [Edit](#edit) ou [AddNew](#addnew).

L’utilisation de NULL pour le premier argument `outputColumn` de la fonction `CDaoFieldExchange`appliquera la fonction à tous les champs, pas **param** champs dans . Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

ne fixera que `outputColumn` des champs à NULL; les champs **de param** ne seront pas affectés.

Pour travailler sur un **param,** vous devez fournir l’adresse réelle de la **param** individuelle que vous souhaitez travailler sur, tels que:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

Cela signifie que vous ne pouvez pas définir `outputColumn` tous les champs **de param** à NULL, comme vous pouvez avec les champs.

`SetFieldDirty`est mis `DoFieldExchange`en œuvre par .

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>CDaoRecordset::SetFieldNull

Appelez cette fonction de membre pour signaler un membre des données sur le terrain de l’enregistrement comme Null (en particulier n’ayant aucune valeur) ou comme non-Null.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Contient l’adresse d’un membre des données sur le terrain dans l’enregistrement ou NULL. Si NULL, tous les membres des données sur le terrain dans le jeu d’enregistrement sont signalés. (C-NULL n’est pas le même que Null dans la terminologie de base de données, ce qui signifie « n’avoir aucune valeur. »)

*bNull (en)*<br/>
Nonzero si le membre des données sur le terrain doit être signalé comme n’ayant aucune valeur (Null). Sinon 0 si le membre des données sur le terrain doit être signalé comme non-Null.

### <a name="remarks"></a>Notes

`SetFieldNull`est utilisé pour les `DoFieldExchange` champs liés dans le mécanisme.

Lorsque vous ajoutez un nouvel enregistrement à un ensemble d’enregistrements, tous les membres des données sur le terrain sont initialement définis à une valeur nulle et signalés comme « sales » (modifiés). Lorsque vous récupérez un enregistrement à partir d’une source de données, ses colonnes ont déjà des valeurs ou sont nulles. S’il n’est pas approprié de faire un champ Null, un [CDaoException](../../mfc/reference/cdaoexception-class.md) est jeté.

Si vous utilisez le mécanisme de double tampon, par exemple, si vous souhaitez spécifiquement désigner un `SetFieldNull` champ de l’enregistrement actuel comme n’ayant pas de valeur, appelez avec *bNull* mis à TRUE pour le signaler comme null. Si un champ était auparavant marqué Null et que vous voulez maintenant lui donner une valeur, il suffit de définir sa nouvelle valeur. Vous n’avez pas à `SetFieldNull`enlever le drapeau Null avec . Pour déterminer si le champ est autorisé à être nul, appelez [IsFieldNullable](#isfieldnullable).

Si vous n’utilisez pas le mécanisme de double tampon, puis changer la valeur du champ ne réglemente pas automatiquement le champ comme sale et non-Null. Vous devez définir spécifiquement les champs sales et non-Null. Le drapeau contenu dans [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) contrôle cette vérification automatique sur le terrain.

Le mécanisme DFX utilise PSEUDONULL. Pour plus d’informations, voir [CDaoFieldExchange:m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
> Appelez cette fonction de membre seulement après que vous avez appelé [Edit](#edit) ou [AddNew](#addnew).

L’utilisation de NULL pour le premier argument `outputColumn` de la fonction `CDaoFieldExchange`n’appliquera la fonction qu’aux champs, et non aux champs **de param** dans . Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

ne fixera que `outputColumn` des champs à NULL; les champs **de param** ne seront pas affectés.

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>CDaoRecordset::SetFieldValue

Appelez cette fonction de membre pour définir la valeur d’un champ, soit par position ordinaire ou en changeant la valeur de la chaîne.

```
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une chaîne contenant le nom d’un champ.

*varValue*<br/>
Une référence à un objet [COleVariant](../../mfc/reference/colevariant-class.md) contenant la valeur du contenu du champ.

*nIndex*<br/>
Un intégrier qui représente la position ordinaire du champ dans la collection Fields du recordet (zéro à base).

*lpszValue*<br/>
Pointeur d’une chaîne contenant la valeur du contenu du champ.

### <a name="remarks"></a>Notes

Utilisez `SetFieldValue` et [GetFieldValue](#getfieldvalue) pour lier dynamiquement les champs au moment de l’exécution plutôt que les colonnes statiquement contraignantes à l’aide du mécanisme [DoFieldExchange.](#dofieldexchange)

Notez que si vous ne créez pas un ensemble d’enregistrements UNICODE, vous devez soit utiliser une forme qui ne contient pas de `SetFieldValue` `COleVariant` paramètre, ou l’objet `COleVariant` doit être explicitement déclaré ANSI. Cela peut être fait en utilisant le [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* `VT_BSTRT` **)** forme de constructeur `COleVariant` avec *vtSrc* mis à (ANSI) ou en utilisant la `VT_BSTRT`fonction [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** avec *vtSrc* réglé à .

Pour obtenir des renseignements connexes, consultez les thèmes « Objet de terrain » et « Propriété de valeur » dans DAO Help.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull

Appelez cette fonction de membre pour définir le champ à une valeur nulle.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice du champ dans le recordet, pour le lookup par indice zéro.

*lpszName (en)*<br/>
Le nom du champ dans le jeu d’enregistrement, pour le lookup par son nom.

### <a name="remarks"></a>Notes

LE NULL n’est pas le même que Null, ce qui, selon la terminologie de la base de données, signifie « n’avoir aucune valeur ».

Pour obtenir des renseignements connexes, consultez les thèmes « Objet de terrain » et « Propriété de valeur » dans DAO Help.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>CDaoRecordset::SetLockingMode

Appelez cette fonction de membre pour définir le type de verrouillage pour le jeu d’enregistrement.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Paramètres

*bPessimiste*<br/>
Un drapeau qui indique le type de verrouillage.

### <a name="remarks"></a>Notes

Lorsque le verrouillage pessimiste est en vigueur, la page 2K contenant l’enregistrement que vous modifiez est verrouillée dès que vous appelez la `Edit` fonction membre. La page est déverrouillée lorsque vous appelez la fonction ou `Update` `Close` la fonction membre ou l’une des opérations Move or Find.

Lorsque le verrouillage optimiste est en vigueur, la page 2K contenant l’enregistrement n’est verrouillée que pendant que l’enregistrement est mis à jour avec la `Update` fonction membre.

Si une page est verrouillée, aucun autre utilisateur ne peut modifier des enregistrements sur la même page. Si vous `SetLockingMode` appelez et passez une valeur non zéro et qu’un autre utilisateur `Edit`a déjà la page verrouillée, une exception est lancée lorsque vous appelez . D’autres utilisateurs peuvent lire les données à partir de pages verrouillées.

Si vous `SetLockingMode` appelez avec une `Update` valeur zéro et que vous appelez plus tard pendant que la page est verrouillée par un autre utilisateur, une exception se produit. Pour voir les modifications apportées à votre enregistrement par `SetBookmark` un autre utilisateur (et perdre vos modifications), appelez la fonction membre avec la valeur de signet de l’enregistrement actuel.

Lorsque vous travaillez avec les sources de données ODBC, le mode de verrouillage est toujours optimiste.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>CDaoRecordset::SetParamValue

Appelez cette fonction de membre pour définir la valeur d’un paramètre dans l’ensemble d’enregistrements au moment de l’exécution.

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
La position numérique du paramètre dans la collection paramètres de la requête.

*var*<br/>
La valeur à définir; voir Remarques.

*lpszName (en)*<br/>
Le nom du paramètre dont vous souhaitez définir la valeur.

### <a name="remarks"></a>Notes

Le paramètre doit déjà avoir été établi dans le cadre de la chaîne SQL du recordet. Vous pouvez accéder au paramètre par son nom ou par sa position d’index dans la collection.

Spécifier la `COleVariant` valeur à définir comme objet. Pour plus d’informations sur la `COleVariant` définition de la valeur et le type souhaités dans votre objet, consultez la classe [COleVariant](../../mfc/reference/colevariant-class.md). Notez que si vous ne créez pas `COleVariant` un ensemble d’enregistrements UNICODE, l’objet doit être explicitement déclaré ANSI. Cela peut être fait en utilisant le [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* `VT_BSTRT` **)** forme de constructeur `COleVariant` avec *vtSrc* mis à (ANSI) ou en utilisant la `VT_BSTRT`fonction [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** avec *vtSrc* réglé à .

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull

Appelez cette fonction de membre pour définir le paramètre à une valeur nulle.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice du champ dans le recordet, pour le lookup par indice zéro.

*lpszName (en)*<br/>
Le nom du champ dans le jeu d’enregistrement, pour le lookup par son nom.

### <a name="remarks"></a>Notes

LE NULL n’est pas le même que Null, ce qui, selon la terminologie de la base de données, signifie « n’avoir aucune valeur ».

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>CDaoRecordset::SetPercentPosition

Appelez cette fonction de membre pour établir une valeur qui modifie l’emplacement approximatif de l’enregistrement actuel dans l’objet de l’enregistrement en fonction d’un pourcentage des enregistrements dans le jeu d’enregistrement.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Paramètres

*fPosition*<br/>
Nombre compris entre 0 et 100.

### <a name="remarks"></a>Notes

Lorsque vous travaillez avec un jeu d’enregistrement de type dynaset ou instantané, d’abord remplir le jeu d’enregistrement en passant au dernier enregistrement avant d’appeler `SetPercentPosition`. Si vous `SetPercentPosition` appelez avant de remplir complètement l’enregistrement, la quantité de mouvement est relative au nombre d’enregistrements consultés comme indiqué par la valeur de [GetRecordCount](#getrecordcount). Vous pouvez passer au dernier `MoveLast`enregistrement en appelant .

Une fois `SetPercentPosition`que vous appelez, l’enregistrement à la position approximative correspondant à cette valeur devient à jour.

> [!NOTE]
> Il `SetPercentPosition` n’est pas recommandé d’appeler à déplacer le dossier actuel à un enregistrement précis dans un enregistrement. Appelez la fonction membre [SetBookmark](#setbookmark) à la place.

Pour obtenir des renseignements connexes, consultez le thème « Propriété de pourcentage » dans DAO Help.

## <a name="cdaorecordsetupdate"></a><a name="update"></a>CDaoRecordset::Mise à jour

Appelez cette fonction de membre `AddNew` `Edit` après un appel à la fonction ou à celui du membre.

```
virtual void Update();
```

### <a name="remarks"></a>Notes

Cet appel est nécessaire `AddNew` `Edit` pour compléter le ou l’opération.

Les `AddNew` `Edit` deux et préparer un tampon de modification dans lequel les données ajoutées ou modifiées sont placées pour l’enregistrement à la source de données. `Update`enregistre les données. Seuls les champs marqués ou détectés tels qu’ils sont modifiés sont mis à jour.

Si la source de données prend `Update` en charge `AddNew` les `Edit` transactions, vous pouvez effectuer la partie d’appel (et de son appel correspondant ou de son appel) d’une transaction.

> [!CAUTION]
> Si vous `Update` appelez sans `AddNew` `Edit`appeler `Update` d’abord ou , jette un `CDaoException`. Si vous `AddNew` `Edit`appelez ou `Update` , vous devez appeler avant d’appeler [MoveNext](#movenext) ou fermer soit le jeu d’enregistrement ou la connexion source de données. Sinon, vos modifications sont perdues sans notification.

Lorsque l’objet de la liste enregistre est verrouillé de façon pessimiste `Edit` dans un environnement multiuscule, l’enregistrement reste verrouillé à partir du moment où la mise à jour est terminée. Si le jeu d’enregistrement est verrouillé avec optimisme, l’enregistrement est verrouillé et comparé à l’enregistrement pré-édité juste avant qu’il ne soit mis à jour dans la base de données. Si le dossier a `Edit`changé `Update` depuis que vous avez appelé, l’opération échoue et MFC jette une exception. Vous pouvez changer le `SetLockingMode`mode de verrouillage avec .

> [!NOTE]
> Le verrouillage optimiste est toujours utilisé sur les formats externes de base de données, tels que ODBC et l’ISAM installable.

Pour plus d’informations, consultez les thèmes "AddNew Method", "CancelUpdate Method", "Delete Method", "LastModified Property", "Update Method", et "EditMode Property" dans DAO Help.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[Classe CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[Classe CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
