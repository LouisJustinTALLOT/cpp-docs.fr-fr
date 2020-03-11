---
title: CDaoFieldExchange (classe)
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: cfffebd16c3c1d62dc4084b962c22911e4b46ae5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867299"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange (classe)

Prend en charge les routines d'échange de champs d'enregistrements DAO (DFX) utilisées par les classes de base de données DAO.

DAO est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

## <a name="syntax"></a>Syntaxe

```
class CDaoFieldExchange
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDaoFieldExchange :: IsValidOperation](#isvalidoperation)|Retourne une valeur différente de zéro si l’opération en cours est appropriée pour le type de champ en cours de mise à jour.|
|[CDaoFieldExchange :: SetFieldType](#setfieldtype)|Spécifie le type de membre de données du jeu d’enregistrements (colonne ou paramètre) représenté par tous les appels suivants aux fonctions DFX jusqu’au prochain appel à `SetFieldType`.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[CDaoFieldExchange :: m_nOperation](#m_noperation)|Opération DFX effectuée par l’appel en cours à la fonction membre `DoFieldExchange` du Recordset.|
|[CDaoFieldExchange :: m_prs](#m_prs)|Pointeur vers le Recordset sur lequel les opérations DFX sont exécutées.|

## <a name="remarks"></a>Notes

`CDaoFieldExchange` n’a pas de classe de base.

Utilisez cette classe si vous écrivez des routines d’échange de données pour des types de données personnalisés ; dans le cas contraire, vous n’utiliserez pas directement cette classe. DFX échange des données entre les membres de données de champ de votre objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) et les champs correspondants de l’enregistrement actif sur la source de données. DFX gère l’échange dans les deux sens, à partir de la source de données et de la source de données. Pour plus d’informations sur l’écriture de routines DFX personnalisées, consultez la [note technique 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) .

> [!NOTE]
>  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur Open Database Connectivity (ODBC). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus puissantes que les classes MFC basées sur ODBC. Les classes basées sur DAO peuvent accéder aux données, notamment via des pilotes ODBC, via leur propre moteur de base de données. Ils prennent également en charge les opérations de langage de définition de données (DDL, Data Definition Language), telles que l’ajout de tables par le biais des classes au lieu d’appeler DAO vous-même.

> [!NOTE]
>  L’échange de champs d’enregistrements DAO (DFX) est très similaire à l’échange de champs d’enregistrement (RFX) dans les classes de base de données MFC basées sur ODBC (`CDatabase`, `CRecordset`). Si vous comprenez RFX, il est facile d’utiliser DFX.

Un objet `CDaoFieldExchange` fournit les informations de contexte nécessaires à l’échange de champs d’enregistrements DAO. les objets `CDaoFieldExchange` prennent en charge un certain nombre d’opérations, y compris les paramètres de liaison et les membres de données de champ, et la définition de différents indicateurs sur les champs de l’enregistrement actif. Les opérations DFX sont effectuées sur les membres de données de classe Recordset de types définis par l' **énumération** **FieldType** dans `CDaoFieldExchange`. Les valeurs possibles de **FieldType** sont les suivantes :

- `CDaoFieldExchange::outputColumn` pour les membres de données de champ.

- `CDaoFieldExchange::param` pour les membres de données de paramètre.

La fonction membre [IsValidOperation](#isvalidoperation) est fournie pour l’écriture de vos propres routines DFX personnalisées. Vous utiliserez fréquemment [SetFieldType](#setfieldtype) dans vos fonctions [CDaoRecordset ::D ofieldexchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) . Pour plus d’informations sur les fonctions DFX globales, consultez [fonctions d’échange de champs d’enregistrement](../../mfc/reference/record-field-exchange-functions.md). Pour plus d’informations sur l’écriture de routines DFX personnalisées pour vos propres types de données, consultez la [note technique 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDaoFieldExchange`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

##  <a name="isvalidoperation"></a>CDaoFieldExchange :: IsValidOperation

Si vous écrivez votre propre fonction DFX, appelez `IsValidOperation` au début de votre fonction pour déterminer si l’opération en cours peut être effectuée sur un type de membre de données de champ particulier (un `CDaoFieldExchange::outputColumn` ou un `CDaoFieldExchange::param`).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération en cours est appropriée pour le type de champ en cours de mise à jour.

### <a name="remarks"></a>Notes

Certaines opérations effectuées par le mécanisme DFX s’appliquent uniquement à l’un des types de champ possibles. Suivez le modèle des fonctions DFX existantes.

Pour plus d’informations sur l’écriture de routines DFX personnalisées, consultez la [note technique 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

##  <a name="m_noperation"></a>CDaoFieldExchange :: m_nOperation

Identifie l’opération à effectuer sur l’objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) associé à l’objet d’échange de champs.

### <a name="remarks"></a>Notes

L’objet `CDaoFieldExchange` fournit le contexte pour un certain nombre d’opérations DFX différentes sur le Recordset.

> [!NOTE]
>  La valeur PSEUDONULL décrite sous les opérations MarkForAddNew et SetFieldNull ci-dessous est une valeur utilisée pour marquer les champs null. Le mécanisme d’échange de champs d’enregistrements DAO (DFX) utilise cette valeur pour déterminer les champs qui ont été explicitement marqués comme null. PSEUDONULL n’est pas requis pour les champs [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) et [COleCurrency](../../mfc/reference/colecurrency-class.md) .

Les valeurs possibles de `m_nOperation` sont les suivantes :

|Opération|Description|
|---------------|-----------------|
|`AddToParameterList`|Génère la clause **Parameters** de l’instruction SQL.|
|`AddToSelectList`|Génère la clause **Select** de l’instruction SQL.|
|`BindField`|Lie un champ de la base de données à un emplacement de mémoire dans votre application.|
|`BindParam`|Définit les valeurs des paramètres de la requête du Recordset.|
|`Fixup`|Définit l’État null pour un champ.|
|`AllocCache`|Alloue le cache utilisé pour rechercher les champs « modifiés » dans le Recordset.|
|`StoreField`|Enregistre l’enregistrement en cours dans le cache.|
|`LoadField`|Restaure les variables de membre de données mises en cache dans le Recordset.|
|`FreeCache`|Libère le cache utilisé pour rechercher les champs « modifiés » dans le jeu d’enregistrements.|
|`SetFieldNull`|Définit l’état d’un champ sur null et la valeur sur PSEUDONULL.|
|`MarkForAddNew`|Marque les champs « impropre » s’ils ne sont pas PSEUDONULL.|
|`MarkForEdit`|Marque les champs « modifiés » s’ils ne correspondent pas au cache.|
|`SetDirtyField`|Définit des valeurs de champ marquées comme « modifiées ».|
|`DumpField`|Vide le contenu d’un champ (débogage uniquement).|
|`MaxDFXOperation`|Utilisé pour la vérification d’entrée.|

##  <a name="m_prs"></a>CDaoFieldExchange :: m_prs

Contient un pointeur vers l’objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) associé à l’objet `CDaoFieldExchange`.

### <a name="remarks"></a>Notes

##  <a name="setfieldtype"></a>CDaoFieldExchange :: SetFieldType

Appelez `SetFieldType` dans la substitution `DoFieldExchange` de la classe `CDaoRecordset`.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Paramètres

*nFieldType*<br/>
Valeur de l' **énumération FieldType**, déclarée dans `CDaoFieldExchange`, qui peut être l’un des éléments suivants :

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Notes

Normalement, ClassWizard écrit cet appel pour vous. Si vous écrivez votre propre fonction et que vous utilisez l’Assistant pour écrire votre fonction `DoFieldExchange`, ajoutez des appels à votre propre fonction en dehors du mappage de champ. Si vous n’utilisez pas l’Assistant, il n’y aura pas de mappage de champ. L’appel précède les appels aux fonctions DFX, un pour chaque membre de données de champ de votre classe, et identifie le type de champ comme `CDaoFieldExchange::outputColumn`.

Si vous paramétrez votre classe Recordset, vous devez ajouter des appels DFX pour tous les membres de données de paramètre (à l’extérieur du mappage de champs) et précéder ces appels par un appel à `SetFieldType`. Transmettez la valeur `CDaoFieldExchange::param`. (Vous pouvez utiliser à la place un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) et définir ses valeurs de paramètre.)

En général, chaque groupe d’appels de fonction DFX associé à des données membres de champ ou de données de paramètre doit être précédé d’un appel à `SetFieldType`. Le paramètre *nFieldType* de chaque appel de `SetFieldType` identifie le type des données membres représentées par les appels de fonction DFX qui suivent l’appel de `SetFieldType`.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)
