---
title: CDaoTableDef, classe
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: 485fe3533916e5e59bc87084f58acfb37368ac32
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418761"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef, classe

Représente la définition stockée d'une table de base ou d'une table attachée.

## <a name="syntax"></a>Syntaxe

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CDaoTableDef :: CDaoTableDef](#cdaotabledef)|Construit un objet `CDaoTableDef`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDaoTableDef :: Append](#append)|Ajoute une nouvelle table à la base de données.|
|[CDaoTableDef :: CanUpdate](#canupdate)|Retourne une valeur différente de zéro si la table peut être mise à jour (vous pouvez modifier la définition des champs ou les propriétés de la table).|
|[CDaoTableDef :: Close](#close)|Ferme une TableDef ouverte.|
|[CDaoTableDef :: Create](#create)|Crée une table qui peut être ajoutée à la base de données à l’aide de [Append](#append).|
|[CDaoTableDef :: CreateField](#createfield)|Appelé pour créer un champ pour une table.|
|[CDaoTableDef :: CreateIndex](#createindex)|Appelé pour créer un index pour une table.|
|[CDaoTableDef ::D eleteField](#deletefield)|Appelé pour supprimer un champ d’une table.|
|[CDaoTableDef ::D eleteIndex](#deleteindex)|Appelé pour supprimer un index d’une table.|
|[CDaoTableDef :: GetAttributes](#getattributes)|Retourne une valeur qui indique une ou plusieurs caractéristiques d’un objet `CDaoTableDef`.|
|[CDaoTableDef :: GetConnect](#getconnect)|Retourne une valeur qui fournit des informations sur la source d’une table.|
|[CDaoTableDef :: GetDateCreated](#getdatecreated)|Retourne la date et l’heure de création de la table de base sous-jacente à un objet `CDaoTableDef`.|
|[CDaoTableDef :: GetDateLastUpdated](#getdatelastupdated)|Retourne la date et l’heure de la dernière modification apportée à la conception de la table de base.|
|[CDaoTableDef :: GetFieldCount](#getfieldcount)|Retourne une valeur qui représente le nombre de champs dans la table.|
|[CDaoTableDef :: GetFieldInfo](#getfieldinfo)|Retourne des types spécifiques d’informations sur les champs de la table.|
|[CDaoTableDef :: GetIndexCount](#getindexcount)|Retourne le nombre d’index de la table.|
|[CDaoTableDef :: GetIndexInfo](#getindexinfo)|Retourne des types spécifiques d’informations sur les index de la table.|
|[CDaoTableDef :: GetName](#getname)|Retourne le nom défini par l’utilisateur de la table.|
|[CDaoTableDef :: GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans la table.|
|[CDaoTableDef :: GetSourceTableName](#getsourcetablename)|Retourne une valeur qui spécifie le nom de la table attachée dans la base de données source.|
|[CDaoTableDef :: GetValidationRule](#getvalidationrule)|Retourne une valeur qui valide les données d’un champ au fur et à mesure qu’elles sont modifiées ou ajoutées à une table.|
|[CDaoTableDef :: GetValidationText](#getvalidationtext)|Retourne une valeur qui spécifie le texte du message affiché par votre application si la valeur d’un objet champ ne satisfait pas la règle de validation spécifiée.|
|[CDaoTableDef :: IsOpen](#isopen)|Retourne une valeur différente de zéro si la table est ouverte.|
|[CDaoTableDef :: Open](#open)|Ouvre un objet TableDef existant stocké dans la collection TableDef’s de la base de données.|
|[CDaoTableDef :: RefreshLink](#refreshlink)|Met à jour les informations de connexion pour une table attachée.|
|[CDaoTableDef :: SetAttributes](#setattributes)|Définit une valeur qui indique une ou plusieurs caractéristiques d’un objet `CDaoTableDef`.|
|[CDaoTableDef :: SetConnect](#setconnect)|Définit une valeur qui fournit des informations sur la source d’une table.|
|[CDaoTableDef :: SetName](#setname)|Définit le nom de la table.|
|[CDaoTableDef :: SetSourceTableName](#setsourcetablename)|Définit une valeur qui spécifie le nom d’une table attachée dans la base de données source.|
|[CDaoTableDef :: SetValidationRule](#setvalidationrule)|Définit une valeur qui valide les données d’un champ au fur et à mesure qu’elles sont modifiées ou ajoutées à une table.|
|[CDaoTableDef :: SetValidationText](#setvalidationtext)|Définit une valeur qui spécifie le texte du message affiché par votre application si la valeur d’un objet champ ne satisfait pas la règle de validation spécifiée.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CDaoTableDef :: m_pDAOTableDef](#m_pdaotabledef)|Pointeur vers l’interface DAO sous-jacente à l’objet TableDef.|
|[CDaoTableDef :: m_pDatabase](#m_pdatabase)|Base de données source pour cette table.|

## <a name="remarks"></a>Notes

Chaque objet de base de données DAO gère une collection, appelée TableDefs, qui contient tous les objets TableDef DAO enregistrés.

Vous manipulez une définition de table à l’aide d’un objet `CDaoTableDef`. Vous pouvez par exemple :

- Examinez la structure de champs et d’index de toute table locale, attachée ou externe dans une base de données.

- Appelez les fonctions membres `SetConnect` et `SetSourceTableName` pour les tables attachées, et utilisez la fonction membre `RefreshLink` pour mettre à jour les connexions aux tables attachées.

- Appelez la fonction membre `CanUpdate` pour déterminer si vous pouvez modifier les définitions de champ dans la table.

- Obtient ou définit des conditions de validation à l’aide des `GetValidationRule` et `SetValidationRule`, ainsi que des fonctions membres `GetValidationText` et `SetValidationText`.

- Utilisez la fonction membre `Open` pour créer un objet de `CDaoRecordset` de type table, feuille de réponse dynamique ou instantané.

    > [!NOTE]
    >  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur Open Database Connectivity (ODBC). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. les classes DAO offrent généralement des fonctionnalités supérieures, car elles sont spécifiques au moteur de base de données Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Pour utiliser des objets TableDef pour travailler avec une table existante ou pour créer une nouvelle table

1. Dans tous les cas, commencez par construire un objet `CDaoTableDef`, en fournissant un pointeur vers un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) auquel la table appartient.

1. Procédez ensuite comme suit, en fonction de vos choix :

   - Pour utiliser une table enregistrée existante, appelez la fonction membre [Open](#open) de l’objet TableDef, en fournissant le nom de la table enregistrée.

   - Pour créer une nouvelle table, appelez la fonction membre [Create](#create) de l’objet TableDef, en fournissant le nom de la table. Appelez [CreateField](#createfield) et [CreateIndex](#createindex) pour ajouter des champs et des index à la table.

   - Appelez [Append](#append) pour enregistrer la table en l’ajoutant à la collection TableDefs de la base de données. `Create` place l’objet TableDef dans un état ouvert, par conséquent, après avoir appelé `Create` vous n’appelez pas `Open`.

        > [!TIP]
        >  Le moyen le plus simple de créer des tables enregistrées consiste à les créer et à les stocker dans votre base de données à l’aide de Microsoft Access. Ensuite, vous pouvez les ouvrir et les utiliser dans votre code MFC.

Pour utiliser l’objet TableDef que vous avez ouvert ou créé, créez et ouvrez un objet `CDaoRecordset`, en spécifiant le nom de l’objet TableDef avec une valeur `dbOpenTable` dans le paramètre *nOpenType* .

Pour utiliser un objet TableDef afin de créer un objet `CDaoRecordset`, vous créez ou ouvrez généralement un objet TableDef comme décrit ci-dessus, puis vous construisez un objet Recordset, en passant un pointeur à votre objet TableDef quand vous appelez [CDaoRecordset :: Open](../../mfc/reference/cdaorecordset-class.md#open). Le TableDef que vous transmettez doit être dans un état ouvert. Pour plus d’informations, consultez la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Lorsque vous avez fini d’utiliser un objet TableDef, appelez sa fonction membre [Close](../../mfc/reference/cdaorecordset-class.md#close) ; Détruisez ensuite l’objet TableDef.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

##  <a name="append"></a>CDaoTableDef :: Append

Appelez cette fonction membre après avoir appelé [Create](#create) pour créer un nouvel objet TableDef afin d’enregistrer l’objet TableDef dans la base de données.

```
virtual void Append();
```

### <a name="remarks"></a>Notes

La fonction ajoute l’objet à la collection TableDefs de la base de données. Vous pouvez utiliser l’objet TableDef comme un objet temporaire tout en le définissant en ne l’ajoutant pas, mais si vous souhaitez l’enregistrer et l’utiliser, vous devez appeler `Append`.

> [!NOTE]
>  Si vous tentez d’ajouter un objet TableDef sans nom (contenant une chaîne null ou vide), MFC lève une exception.

Pour obtenir des informations connexes, consultez la rubrique « méthode Append » dans l’aide de DAO.

##  <a name="canupdate"></a>CDaoTableDef :: CanUpdate

Appelez cette fonction membre pour déterminer si la définition de la table sous-jacente à un objet `CDaoTableDef` peut être modifiée.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la structure de table (schéma) peut être modifiée (ajouter ou supprimer des champs et des index); sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, une table nouvellement créée sous-jacente à un objet `CDaoTableDef` peut être mise à jour, et une table attachée sous-jacente à un objet `CDaoTableDef` ne peut pas être mise à jour. Un objet `CDaoTableDef` peut être mis à jour, même si le jeu d’enregistrements résultant ne peut pas être mis à jour.

Pour obtenir des informations connexes, consultez la rubrique « propriété pouvant être mise à jour » dans l’aide de DAO.

##  <a name="cdaotabledef"></a>CDaoTableDef :: CDaoTableDef

Construit un objet `CDaoTableDef`.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Paramètres

*pDatabase*<br/>
Pointeur vers un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Notes

Après avoir construit l’objet, vous devez appeler la fonction membre [Create](#create) ou [Open](#open) . Lorsque vous avez terminé avec l’objet, vous devez appeler sa fonction membre [Close](#close) et détruire l’objet `CDaoTableDef`.

##  <a name="close"></a>CDaoTableDef :: Close

Appelez cette fonction membre pour fermer et libérer l’objet TableDef.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

En général, après avoir appelé `Close`, vous supprimez l’objet TableDef s’il a été alloué avec **New**.

Vous pouvez appeler [Open](#open) à nouveau après avoir appelé `Close`. Cela vous permet de réutiliser l’objet TableDef.

Pour obtenir des informations connexes, consultez la rubrique « méthode Close » dans l’aide de DAO.

##  <a name="create"></a>CDaoTableDef :: Create

Appelez cette fonction membre pour créer une nouvelle table enregistrée.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Pointeur vers une chaîne contenant le nom de la table.

*lAttributes*<br/>
Valeur correspondant aux caractéristiques de la table représentée par l’objet TableDef. Vous pouvez utiliser l’opérateur or au niveau du bit pour combiner l’une des constantes suivantes :

|Constant|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID d’utilisateur et le mot de passe de la table attachée sont enregistrés avec les informations de connexion.|
|`dbSystemObject`|Indique que la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique que la table est une table cachée fournie par le moteur de base de données Microsoft Jet.|

*lpszSrcTable*<br/>
Pointeur vers une chaîne contenant le nom de la table source. Par défaut, cette valeur est initialisée comme NULL.

*lpszConnect*<br/>
Pointeur vers une chaîne contenant la chaîne de connexion par défaut. Par défaut, cette valeur est initialisée comme NULL.

### <a name="remarks"></a>Notes

Une fois que vous avez nommé TableDef, vous pouvez appeler [Append](#append) pour enregistrer l’objet TableDef dans la collection TableDefs de la base de données. Après l’appel de `Append`, l’objet TableDef est dans un état ouvert et vous pouvez l’utiliser pour créer un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

Pour obtenir des informations connexes, consultez la rubrique « méthode CreateTableDef » dans l’aide de DAO.

##  <a name="createfield"></a>CDaoTableDef :: CreateField

Appelez cette fonction membre pour ajouter un champ à la table.

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Pointeur vers une expression de chaîne spécifiant le nom de ce champ.

*nType*<br/>
Valeur indiquant le type de données du champ. Le paramètre peut prendre l’une des valeurs suivantes :

|Type|Taille (en octets)|Description|
|----------|--------------------|-----------------|
|`dbBoolean`|1 octet|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Devise ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Date/heure ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texte ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objet OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) ou [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Mémo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Valeur qui indique la taille maximale, en octets, d’un champ qui contient du texte ou la taille fixe d’un champ qui contient du texte ou des valeurs numériques. Le paramètre *lSize* est ignoré pour tous les champs, sauf les champs de texte.

*lAttributes*<br/>
Valeur correspondant aux caractéristiques du champ et qui peut être combinée à l’aide d’une opération or au niveau du bit.

|Constant|Description|
|--------------|-----------------|
|`dbFixedField`|La taille du champ est fixe (valeur par défaut pour les champs numériques).|
|`dbVariableField`|La taille de champ est variable (champs de texte uniquement).|
|`dbAutoIncrField`|La valeur de champ pour les nouveaux enregistrements est automatiquement incrémentée à un entier long unique qui ne peut pas être modifié. Pris en charge uniquement pour les tables de base de données Microsoft Jet.|
|`dbUpdatableField`|La valeur du champ peut être modifiée.|
|`dbDescending`|Le champ est trié par ordre décroissant (Z-A ou 100-0) (s’applique uniquement à un objet de champ dans une collection de champs d’un objet d’index). Si vous omettez cette constante, le champ est trié dans l’ordre croissant (A-Z ou 0-100) (valeur par défaut).|

*FieldInfo*<br/>
Référence à une structure [cdaofieldinfo,](../../mfc/reference/cdaofieldinfo-structure.md) .

### <a name="remarks"></a>Notes

Un objet `DAOField` (OLE) est créé et ajouté à la collection Fields de l’objet `DAOTableDef` (OLE). Outre son utilisation pour l’examen des propriétés de l’objet, vous pouvez également utiliser `CDaoFieldInfo` pour construire un paramètre d’entrée pour la création de nouveaux champs dans un objet TableDef. La première version de `CreateField` est plus simple à utiliser, mais si vous souhaitez un contrôle plus fin, vous pouvez utiliser la deuxième version de `CreateField`, qui prend un paramètre `CDaoFieldInfo`.

Si vous utilisez la version de `CreateField` qui accepte un paramètre `CDaoFieldInfo`, vous devez définir avec soin chacun des membres suivants de la structure `CDaoFieldInfo` :

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Les membres restants de `CDaoFieldInfo` doivent avoir la valeur **0**, false ou une chaîne vide, en fonction du membre, ou un `CDaoException` peut se produire.

Pour obtenir des informations connexes, consultez la rubrique « méthode CreateField » dans l’aide de DAO.

##  <a name="createindex"></a>CDaoTableDef :: CreateIndex

Appelez cette fonction pour ajouter un index à une table.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Paramètres

*indexinfo*<br/>
Référence à une structure [cdaoindexinfo,](../../mfc/reference/cdaoindexinfo-structure.md) .

### <a name="remarks"></a>Notes

Les index spécifient l’ordre des enregistrements accessibles à partir des tables de base de données et si les enregistrements en double sont acceptés ou non. Les index offrent également un accès efficace aux données.

Vous n’êtes pas obligé de créer des index pour les tables, mais dans les grandes tables non indexées, l’accès à un enregistrement spécifique ou la création d’un jeu d’enregistrements peut prendre beaucoup de temps. D’un autre côté, la création d’un trop grand nombre d’index ralentit les opérations de mise à jour, d’ajout et de suppression, car tous les index sont automatiquement mis à jour. Tenez compte de ces facteurs lorsque vous décidez des index à créer.

Les membres suivants de la structure `CDaoIndexInfo` doivent être définis :

- `m_strName` un nom doit être fourni.

- `m_pFieldInfos` doit pointer vers un tableau de structures `CDaoIndexFieldInfo`.

- `m_nFields` devez spécifier le nombre de champs dans le tableau de structures de `CDaoFieldInfo`.

Les membres restants seront ignorés s’ils sont définis sur FALSe. En outre, le membre `m_lDistinctCount` est ignoré lors de la création de l’index.

##  <a name="deletefield"></a>CDaoTableDef ::D eleteField

Appelez cette fonction membre pour supprimer un champ et le rendre inaccessible.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Pointeur vers une expression de chaîne qui est le nom d’un champ existant.

*nIndex*<br/>
Index du champ dans la collection de champs de base zéro de la table, pour la recherche par index.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction membre sur un nouvel objet qui n’a pas été ajouté à la base de données ou lorsque [CanUpdate](#canupdate) retourne une valeur différente de zéro.

Pour obtenir des informations connexes, consultez la rubrique « méthode Delete » dans l’aide de DAO.

##  <a name="deleteindex"></a>CDaoTableDef ::D eleteIndex

Appelez cette fonction membre pour supprimer un index dans une table sous-jacente.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Pointeur vers une expression de chaîne qui est le nom d’un index existant.

*nIndex*<br/>
Index de tableau de l’objet index dans la collection TableDefs de base zéro de la base de données, pour la recherche par index.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction membre sur un nouvel objet qui n’a pas été ajouté à la base de données ou lorsque [CanUpdate](#canupdate) retourne une valeur différente de zéro.

Pour obtenir des informations connexes, consultez la rubrique « méthode Delete » dans l’aide de DAO.

##  <a name="getattributes"></a>CDaoTableDef :: GetAttributes

Pour un objet `CDaoTableDef`, la valeur de retour spécifie les caractéristiques de la table représentée par l’objet `CDaoTableDef` et peut être la somme de ces constantes :

```
long GetAttributes();
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur qui indique une ou plusieurs caractéristiques d’un objet `CDaoTableDef`.

### <a name="remarks"></a>Notes

|Constant|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID d’utilisateur et le mot de passe de la table attachée sont enregistrés avec les informations de connexion.|
|`dbSystemObject`|Indique que la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique que la table est une table cachée fournie par le moteur de base de données Microsoft Jet.|
|`dbAttachedTable`|Indique que la table est une table attachée à partir d’une base de données non ODBC, telle qu’une base de données Paradox.|
|`dbAttachedODBC`|Indique que la table est une table attachée à partir d’une base de données ODBC, par exemple Microsoft SQL Server.|

Une table système est une table créée par le moteur de base de données Microsoft Jet pour contenir différentes informations internes.

Une table masquée est une table créée pour une utilisation temporaire par le moteur de base de données Microsoft Jet.

Pour obtenir des informations connexes, consultez la rubrique « propriété Attributes » dans l’aide de DAO.

##  <a name="getconnect"></a>CDaoTableDef :: GetConnect

Appelez cette fonction membre pour obtenir la chaîne de connexion d’une source de données.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur de retour

Objet `CString` contenant le chemin d’accès et le type de base de données de la table.

### <a name="remarks"></a>Notes

Pour un objet `CDaoTableDef` qui représente une table attachée, l’objet `CString` se compose d’une ou de deux parties (un spécificateur de type de base de données et d’un chemin d’accès à la base de données).

Le chemin d’accès, comme indiqué dans le tableau ci-dessous, est le chemin d’accès complet du répertoire contenant les fichiers de base de données et doit être précédé de l’identificateur « DATABASE = ». Dans certains cas (comme avec les bases de données Microsoft Jet et Microsoft Excel), un nom de fichier spécifique est inclus dans l’argument de chemin d’accès de la base de données.

La table dans [CDaoTableDef :: SetConnect](#setconnect) affiche les types de bases de données possibles et les spécificateurs et les chemins d’accès de base de données correspondants :

Pour les tables de base de base de données Microsoft Jet, le spécificateur est une chaîne vide ("").

Si un mot de passe est requis mais n’est pas fourni, le pilote ODBC affiche une boîte de dialogue de connexion la première fois qu’un utilisateur accède à une table, puis de nouveau si la connexion est fermée et rouverte. Si une table attachée possède l’attribut `dbAttachSavePWD`, l’invite de connexion ne s’affiche pas lorsque la table est rouverte.

Pour obtenir des informations connexes, consultez la rubrique « Connect Property » dans l’aide de DAO.

##  <a name="getdatecreated"></a>CDaoTableDef :: GetDateCreated

Appelez cette fonction pour déterminer la date et l’heure de création de la table sous-jacente de l’objet `CDaoTableDef`.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valeur de retour

Valeur contenant la date et l’heure de la création de la table sous-jacente de l’objet `CDaoTableDef`.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mise à jour pour la dernière fois. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers afin d’éviter les incohérences. autrement dit, tous les clients doivent utiliser une source de temps « standard », par exemple à partir d’un serveur.

Pour obtenir des informations connexes, consultez la rubrique « Propriétés DateCreated, LastUpdated » dans l’aide de DAO.

##  <a name="getdatelastupdated"></a>CDaoTableDef :: GetDateLastUpdated

Appelez cette fonction pour déterminer la date et l’heure de la dernière mise à jour de la table sous-jacente de l’objet `CDaoTableDef`.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui contient la date et l’heure de la dernière mise à jour de la table sous-jacente de l’objet `CDaoTableDef`.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mise à jour pour la dernière fois. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers afin d’éviter les incohérences. autrement dit, tous les clients doivent utiliser une source de temps « standard », par exemple à partir d’un serveur.

Pour obtenir des informations connexes, consultez la rubrique « Propriétés DateCreated, LastUpdated » dans l’aide de DAO.

##  <a name="getfieldcount"></a>CDaoTableDef :: GetFieldCount

Appelez cette fonction membre pour récupérer le nombre de champs définis dans la table.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre de champs dans la table.

### <a name="remarks"></a>Notes

Si sa valeur est 0, il n’y a pas d’objets dans la collection.

Pour obtenir des informations connexes, consultez la rubrique « propriété Count » dans l’aide de DAO.

##  <a name="getfieldinfo"></a>CDaoTableDef :: GetFieldInfo

Appelez cette fonction membre pour obtenir différents genres d’informations sur un champ défini dans l’objet TableDef.

```
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
Index de l’objet de champ dans la collection de champs de base zéro de la table, pour la recherche par index.

*FieldInfo*<br/>
Référence à une structure [cdaofieldinfo,](../../mfc/reference/cdaofieldinfo-structure.md) .

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives au champ à récupérer. Les options disponibles sont répertoriées ici, ainsi que ce qu’elles provoquent le retour de la fonction :

- `AFX_DAO_PRIMARY_INFO` (par défaut) nom, type, taille et attributs. Utilisez cette option pour des performances plus rapides.

- `AFX_DAO_SECONDARY_INFO` informations principales, plus : position ordinale, obligatoire, autoriser la longueur nulle, ordre de classement, nom étranger, champ source, table source

- `AFX_DAO_ALL_INFO` les informations primaires et secondaires, ainsi que la règle de validation, le texte de validation, la valeur par défaut

*lpszName*<br/>
Pointeur vers le nom de l’objet de champ, pour la recherche par nom. Le nom est une chaîne comportant jusqu’à 64 caractères qui renomme le champ de façon unique.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un champ par index. L’autre version vous permet de rechercher un champ par nom.

Pour obtenir une description des informations retournées, consultez la structure [cdaofieldinfo,](../../mfc/reference/cdaofieldinfo-structure.md) . Cette structure a des membres qui correspondent aux éléments d’informations énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous recevez également des informations sur les niveaux précédents.

Pour obtenir des informations connexes, consultez la rubrique « propriété Attributes » dans l’aide de DAO.

##  <a name="getindexcount"></a>CDaoTableDef :: GetIndexCount

Appelez cette fonction membre pour obtenir le nombre d’index d’une table.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’index de la table.

### <a name="remarks"></a>Notes

Si sa valeur est 0, il n’y a pas d’index dans la collection.

Pour obtenir des informations connexes, consultez la rubrique « propriété Count » dans l’aide de DAO.

##  <a name="getindexinfo"></a>CDaoTableDef :: GetIndexInfo

Appelez cette fonction membre pour obtenir différents genres d’informations sur un index défini dans l’objet TableDef.

```
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
Index numérique de l’objet d’index dans la collection d’index de base zéro de la table, pour la recherche en fonction de sa position dans la collection.

*indexinfo*<br/>
Référence à une structure [cdaoindexinfo,](../../mfc/reference/cdaoindexinfo-structure.md) .

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives à l’index à récupérer. Les options disponibles sont répertoriées ici, ainsi que ce qu’elles provoquent le retour de la fonction :

- Nom de `AFX_DAO_PRIMARY_INFO`, informations de champ, champs. Utilisez cette option pour des performances plus rapides.

- `AFX_DAO_SECONDARY_INFO` informations principales, plus : principal, unique, cluster, ignorer les valeurs NULL, obligatoire, étranger

- `AFX_DAO_ALL_INFO` les informations primaires et secondaires, plus : nombre distinct

*lpszName*<br/>
Pointeur vers le nom de l’objet d’index, pour la recherche par nom.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un index en fonction de sa position dans la collection. L’autre version vous permet de rechercher un index par nom.

Pour obtenir une description des informations retournées, consultez la structure [cdaoindexinfo,](../../mfc/reference/cdaoindexinfo-structure.md) . Cette structure a des membres qui correspondent aux éléments d’informations énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous recevez également des informations sur les niveaux précédents.

Pour obtenir des informations connexes, consultez la rubrique « propriété Attributes » dans l’aide de DAO.

##  <a name="getname"></a>CDaoTableDef :: GetName

Appelez cette fonction membre pour obtenir le nom défini par l’utilisateur de la table sous-jacente.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Nom défini par l’utilisateur pour une table.

### <a name="remarks"></a>Notes

Ce nom commence par une lettre et peut contenir jusqu’à 64 caractères. Elle peut inclure des nombres et des traits de soulignement, mais ne peut pas inclure de signes de ponctuation ou d’espace.

Pour obtenir des informations connexes, consultez la rubrique « propriété Name » dans l’aide de DAO.

##  <a name="getrecordcount"></a>CDaoTableDef :: GetRecordCount

Appelez cette fonction membre pour connaître le nombre d’enregistrements dans un objet `CDaoTableDef`.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’enregistrements accessibles dans un objet TableDef.

### <a name="remarks"></a>Notes

L’appel de `GetRecordCount` pour un objet `CDaoTableDef` de type table reflète le nombre approximatif d’enregistrements dans la table et est immédiatement affecté au fur et à mesure de l’ajout et de la suppression d’enregistrements de table. Les transactions restaurées apparaissent dans le nombre d’enregistrements tant que vous n’appelez pas [CDaoWorkSpace :: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Un objet `CDaoTableDef` sans enregistrement a une valeur de propriété nombre d’enregistrements égale à 0. Lorsque vous utilisez des tables attachées ou des bases de données ODBC, `GetRecordCount` retourne toujours-1.

Pour obtenir des informations connexes, consultez la rubrique « propriété RecordCount » dans l’aide de DAO.

##  <a name="getsourcetablename"></a>CDaoTableDef :: GetSourceTableName

Appelez cette fonction membre pour récupérer le nom d’une table attachée dans une base de données source.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Valeur de retour

Objet `CString` qui spécifie le nom de la source d’une table attachée, ou une chaîne vide s’il s’agit d’une table de données native.

### <a name="remarks"></a>Notes

Une table attachée est une table d’une autre base de données liée à une base de données Microsoft Jet. Les données des tables attachées restent dans la base de données externe, où elles peuvent être manipulées par d’autres applications.

Pour obtenir des informations connexes, consultez la rubrique « propriété SourceTableName » dans l’aide de DAO.

##  <a name="getvalidationrule"></a>CDaoTableDef :: GetValidationRule

Appelez cette fonction membre pour récupérer la règle de validation d’un objet TableDef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valeur de retour

Objet `CString` qui valide les données d’un champ au fur et à mesure qu’elles sont modifiées ou ajoutées à une table.

### <a name="remarks"></a>Notes

Les règles de validation sont utilisées dans le cadre des opérations de mise à jour. Si un objet TableDef contient une règle de validation, les mises à jour apportées à cet objet TableDef doivent correspondre à des critères prédéterminés avant que les données ne soient modifiées. Si la modification ne correspond pas aux critères, une exception contenant la valeur de [GetValidationText](#getvalidationtext) est levée. Pour un objet `CDaoTableDef`, ce `CString` est en lecture seule pour une table attachée et en lecture/écriture pour une table de base.

Pour obtenir des informations connexes, consultez la rubrique « propriété ValidationRule » dans l’aide de DAO.

##  <a name="getvalidationtext"></a>CDaoTableDef :: GetValidationText

Appelez cette fonction pour récupérer la chaîne à afficher lorsqu’un utilisateur entre des données qui ne correspondent pas à la règle de validation.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valeur de retour

Objet `CString` qui spécifie le texte affiché si l’utilisateur entre des données qui ne correspondent pas à la règle de validation.

### <a name="remarks"></a>Notes

Pour un objet `CDaoTableDef`, ce `CString` est en lecture seule pour une table attachée et en lecture/écriture pour une table de base.

Pour obtenir des informations connexes, consultez la rubrique « propriété MessageSiErreur » dans l’aide de DAO.

##  <a name="isopen"></a>CDaoTableDef :: IsOpen

Appelez cette fonction membre pour déterminer si l’objet `CDaoTableDef` est actuellement ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `CDaoTableDef` est ouvert ; Sinon, 0.

### <a name="remarks"></a>Notes

##  <a name="m_pdatabase"></a>CDaoTableDef :: m_pDatabase

Contient un pointeur vers l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) pour cette table.

### <a name="remarks"></a>Notes

##  <a name="m_pdaotabledef"></a>CDaoTableDef :: m_pDAOTableDef

Contient un pointeur vers l’interface OLE pour l’objet TableDef DAO sous-jacent de l’objet `CDaoTableDef`.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous devez accéder directement à l’interface DAO.

##  <a name="open"></a>CDaoTableDef :: Open

Appelez cette fonction membre pour ouvrir un objet TableDef précédemment enregistré dans la collection TableDef’s de la base de données.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Pointeur vers une chaîne qui spécifie un nom de table.

### <a name="remarks"></a>Notes

##  <a name="refreshlink"></a>CDaoTableDef :: RefreshLink

Appelez cette fonction membre pour mettre à jour les informations de connexion pour une table attachée.

```
void RefreshLink();
```

### <a name="remarks"></a>Notes

Vous modifiez les informations de connexion d’une table attachée en appelant [SetConnect](#setconnect) sur l’objet `CDaoTableDef` correspondant, puis en utilisant la fonction membre `RefreshLink` pour mettre à jour les informations. Lorsque vous appelez `RefreshLink`, les propriétés de la table attachée ne sont pas modifiées.

Pour forcer l’application des informations de connexion modifiées, tous les objets [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ouverts basés sur ce TableDef doivent être fermés.

Pour obtenir des informations connexes, consultez la rubrique « méthode RefreshLink » dans l’aide de DAO.

##  <a name="setattributes"></a>CDaoTableDef :: SetAttributes

Définit une valeur qui indique une ou plusieurs caractéristiques d’un objet `CDaoTableDef`.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Paramètres

*lAttributes*<br/>
Les caractéristiques de la table représentée par l’objet `CDaoTableDef` et peuvent être une somme de ces constantes :

|Constant|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID d’utilisateur et le mot de passe de la table attachée sont enregistrés avec les informations de connexion.|
|`dbSystemObject`|Indique que la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique que la table est une table cachée fournie par le moteur de base de données Microsoft Jet.|

### <a name="remarks"></a>Notes

Lors de la définition de plusieurs attributs, vous pouvez les combiner en additionnant les constantes appropriées à l’aide de l’opérateur or au niveau du bit. La définition de `dbAttachExclusive` sur une table non attachée génère une exception. La combinaison des valeurs suivantes produit également une exception :

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Pour obtenir des informations connexes, consultez la rubrique « propriété Attributes » dans l’aide de DAO.

##  <a name="setconnect"></a>CDaoTableDef :: SetConnect

Pour un objet `CDaoTableDef` qui représente une table attachée, l’objet String se compose d’une ou de deux parties (un spécificateur de type de base de données et un chemin d’accès à la base de données).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Paramètres

*lpszConnect*<br/>
Pointeur vers une expression de chaîne qui spécifie des paramètres supplémentaires à passer à ODBC ou à des pilotes ISAM installables.

### <a name="remarks"></a>Notes

Le chemin d’accès, comme indiqué dans le tableau ci-dessous, est le chemin d’accès complet du répertoire contenant les fichiers de base de données et doit être précédé de l’identificateur « DATABASE = ». Dans certains cas (comme avec les bases de données Microsoft Jet et Microsoft Excel), un nom de fichier spécifique est inclus dans l’argument de chemin d’accès de la base de données.

> [!NOTE]
>  N’incluez pas d’espace blanc autour des instructions de chemin d’accès de connexion équivalente sous la forme « DATABASE = Drive :\\\path ». Cela entraîne la levée d’une exception et l’échec de la connexion.

Le tableau suivant répertorie les types de bases de données possibles et les spécificateurs et les chemins d’accès de base de données correspondants :

|Type de base de données|Spécificateur|Path|
|-------------------|---------------|----------|
|Base de données utilisant le moteur de base de données Jet|« [`database`]; »|«`drive`:\\*chemin* de \ \\\ *nom de fichier*. MDB|
|dBASE III|« dBASE III ; »|« `drive`:\\*chemin d’accès*\ »|
|dBASE IV|« dBASE IV ; »|« `drive`:\\*chemin d’accès*\ »|
|dBASE 5|« dBASE 5,0 ; »|« `drive`:\\*chemin d’accès*\ »|
|Paradox 3. x|« Paradox 3. x ; »|« `drive`:\\*chemin d’accès*\ »|
|Paradox 4. x|« Paradox 4. x ; »|« `drive`:\\*chemin d’accès*\ »|
|Paradox 5. x|« Paradox 5. x ; »|« `drive`:\\*chemin d’accès*\ »|
|Excel 3,0|« Excel 3,0 ; »|«`drive`:\\*chemin* de \ \\\ *nom de fichier*. XLS|
|Excel 4,0|« Excel 4,0 ; »|«`drive`:\\*chemin* de \ \\\ *nom de fichier*. XLS|
|Excel 5,0 ou Excel 95|« Excel 5,0 ; »|«`drive`:\\*chemin* de \ \\\ *nom de fichier*. XLS|
|Excel 97|« Excel 8,0 ; »|«`drive`:\\*chemin d’accès* \ \ *nom de fichier*. XLS|
|Importation HTML|« Importation HTML ; »|« `drive`:\\*chemin d’accès* \ \ *nom de fichier*»|
|Exportation HTML|« Exportation HTML ; »|« `drive`:\\*chemin d’accès*\ »|
|Texte|« Texte ; »|« lecteur :\\\path »|
|ODBC|ODBC BASE de données = `database`; UID = *User*; PWD = *mot de passe*; DSN = *DataSourceName ;* LOGINTIMEOUT = *secondes ;* » (Il se peut qu’il ne s’agit pas d’une chaîne de connexion complète pour tous les serveurs ; il s’agit simplement d’un exemple. Il est très important de ne pas avoir d’espace entre les paramètres.)|None|
|Exchange|Échanger<br /><br /> MAPILEVEL = *folderPath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [PROFILe = *Profile*;]<br /><br /> [PWD = *mot de passe*;]<br /><br /> [DATABASE = `database`;]»|*«lecteur*:\\*chemin d’accès* \ \\\ *nom de fichier*. MDB|

> [!NOTE]
>  Btrieve n’est plus pris en charge à partir de DAO 3,5.

Vous devez utiliser une double barre oblique inverse (\\\\) dans les chaînes de connexion. Si vous avez modifié les propriétés d’une connexion existante à l’aide de `SetConnect`, vous devez ensuite appeler [RefreshLink](#refreshlink). Si vous initialisez les propriétés de connexion à l’aide de `SetConnect`, vous n’avez pas besoin d’appeler `RefreshLink`, mais si vous le souhaitez, vous devez d’abord ajouter l’objet TableDef.

Si un mot de passe est requis mais n’est pas fourni, le pilote ODBC affiche une boîte de dialogue de connexion la première fois qu’un utilisateur accède à une table, puis de nouveau si la connexion est fermée et rouverte.

Vous pouvez définir la chaîne de connexion pour un objet `CDaoTableDef` en fournissant un argument source à la fonction membre `Create`. Vous pouvez vérifier le paramètre pour déterminer le type, le chemin d’accès, l’ID utilisateur, le mot de passe ou la source de données ODBC de la base de données. Pour plus d’informations, consultez la documentation relative au pilote spécifique.

Pour obtenir des informations connexes, consultez la rubrique « Connect Property » dans l’aide de DAO.

##  <a name="setname"></a>CDaoTableDef :: SetName

Appelez cette fonction membre pour définir un nom défini par l’utilisateur pour une table.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Pointeur vers une expression de chaîne qui spécifie un nom pour une table.

### <a name="remarks"></a>Notes

Le nom doit commencer par une lettre et peut contenir jusqu’à 64 caractères. Elle peut inclure des nombres et des traits de soulignement, mais ne peut pas inclure de signes de ponctuation ou d’espace.

Pour obtenir des informations connexes, consultez la rubrique « propriété Name » dans l’aide de DAO.

##  <a name="setsourcetablename"></a>CDaoTableDef :: SetSourceTableName

Appelez cette fonction membre pour spécifier le nom d’une table attachée ou le nom de la table de base sur laquelle l’objet `CDaoTableDef` est basé, tel qu’il existe dans la source d’origine des données.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Paramètres

*lpszSrcTableName*<br/>
Pointeur vers une expression de chaîne qui spécifie un nom de table dans la base de données externe. Pour une table de base, le paramètre est une chaîne vide ("").

### <a name="remarks"></a>Notes

Vous devez ensuite appeler [RefreshLink](#refreshlink). Ce paramètre de propriété est vide pour une table de base et en lecture/écriture pour une table attachée ou un objet qui n’est pas ajouté à une collection.

Pour obtenir des informations connexes, consultez la rubrique « propriété SourceTableName » dans l’aide de DAO.

##  <a name="setvalidationrule"></a>CDaoTableDef :: SetValidationRule

Appelez cette fonction membre pour définir une règle de validation pour un objet TableDef.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Paramètres

*lpszValidationRule*<br/>
Pointeur vers une expression de chaîne qui valide une opération.

### <a name="remarks"></a>Notes

Les règles de validation sont utilisées dans le cadre des opérations de mise à jour. Si un objet TableDef contient une règle de validation, les mises à jour apportées à cet objet TableDef doivent correspondre à des critères prédéterminés avant que les données ne soient modifiées. Si la modification ne correspond pas aux critères, une exception contenant le texte de [GetValidationText](#getvalidationtext) s’affiche.

La validation est prise en charge uniquement pour les bases de données qui utilisent le moteur de base de données Microsoft Jet. L’expression ne peut pas faire référence à des fonctions définies par l’utilisateur, à des fonctions d’agrégation de domaine, à des fonctions d’agrégation SQL ou à des requêtes. Une règle de validation pour un objet `CDaoTableDef` peut faire référence à plusieurs champs de cet objet.

Par exemple, pour les champs nommés *hire_date* et *termination_date*, une règle de validation peut être :

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Pour obtenir des informations connexes, consultez la rubrique « propriété ValidationRule » dans l’aide de DAO.

##  <a name="setvalidationtext"></a>CDaoTableDef :: SetValidationText

Appelez cette fonction membre pour définir le texte d’exception d’une règle de validation pour un objet `CDaoTableDef` avec une table de base sous-jacente prise en charge par le moteur de base de données Microsoft Jet.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Paramètres

*lpszValidationText*<br/>
Pointeur vers une expression de chaîne qui spécifie le texte affiché si les données entrées ne sont pas valides.

### <a name="remarks"></a>Notes

Vous ne pouvez pas définir le texte de validation d’une table attachée.

Pour obtenir des informations connexes, consultez la rubrique « propriété MessageSiErreur » dans l’aide de DAO.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)
