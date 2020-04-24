---
title: Classe CDaoFieldExchange
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
ms.openlocfilehash: 86f12f78338d1c60e3dd13614ccedc2868f28d81
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754720"
---
# <a name="cdaofieldexchange-class"></a>Classe CDaoFieldExchange

Prend en charge les routines d'échange de champs d'enregistrements DAO (DFX) utilisées par les classes de base de données DAO.

DAO est soutenu par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète.

## <a name="syntax"></a>Syntaxe

```
class CDaoFieldExchange
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Retourne nonzero si l’opération actuelle est appropriée pour le type de champ mis à jour.|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Spécifie le type de membre des données de l’enregistrement — colonne ou paramètre `SetFieldType`— représenté par tous les appels ultérieurs aux fonctions DFX jusqu’au prochain appel à .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|L’opération DFX effectuée par l’appel actuel `DoFieldExchange` à la fonction de membre du recordet.|
|[CDaoFieldExchange::m_prs](#m_prs)|Un pointeur à l’enregistrement sur lequel les opérations DFX sont effectuées.|

## <a name="remarks"></a>Notes

`CDaoFieldExchange`n’a pas de classe de base.

Utilisez cette classe si vous écrivez des routines d’échange de données pour des types de données personnalisés; sinon, vous n’utiliserez pas directement cette classe. DFX échange des données entre les membres des données de terrain de votre objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) et les champs correspondants de l’enregistrement actuel sur la source de données. DFX gère l’échange dans les deux directions, de la source de données et de la source de données. Voir [La note technique 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) pour plus d’informations sur l’écriture de routines DFX personnalisées.

> [!NOTE]
> Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur la connectivité open Database (ODBC). Tous les noms de classe de base de données DAO ont le préfixe "CDao". Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus capables que les classes MFC basées sur ODBC. Les classes basées sur DAO peuvent accéder aux données, y compris par l’intermédiaire des pilotes ODBC, via leur propre moteur de base de données. Ils prennent également en charge les opérations de langage de définition des données (DDL), telles que l’ajout de tables via les classes au lieu d’avoir à appeler DAO vous-même.

> [!NOTE]
> DAO record field exchange (DFX) est très similaire à l’échange record sur le terrain `CDatabase` `CRecordset`(RFX) dans les classes de base de données MFC basée à ODBC ( , ). Si vous comprenez RFX, vous trouverez qu’il est facile d’utiliser DFX.

Un `CDaoFieldExchange` objet fournit les informations contextuelles nécessaires à l’échange de terrain des dossiers DAO. `CDaoFieldExchange`les objets prennent en charge un certain nombre d’opérations, y compris les paramètres contraignants et les membres des données sur le terrain et l’établissement de divers drapeaux sur les champs du dossier actuel. Les opérations DFX sont effectuées sur des données de classe record `CDaoFieldExchange`des membres de types définis par **l’enum** **FieldType** dans . Les valeurs possibles **de FieldType** sont les :

- `CDaoFieldExchange::outputColumn`pour les membres des données sur le terrain.

- `CDaoFieldExchange::param`pour les membres des données de paramètres.

La fonction membre [IsValidOperation](#isvalidoperation) est prévue pour l’écriture de vos propres routines DFX personnalisées. Vous utiliserez fréquemment [SetFieldType](#setfieldtype) dans vos fonctions [CDaoRecordset::DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) Pour plus de détails sur les fonctions mondiales DFX, voir [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md). Pour plus d’informations sur l’écriture de routines DFX personnalisées pour vos propres types de données, voir [Note technique 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDaoFieldExchange`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

Si vous écrivez votre propre `IsValidOperation` fonction DFX, appelez au début de votre fonction pour déterminer si `CDaoFieldExchange::outputColumn` l’opération actuelle peut être effectuée sur un type particulier de membre de données sur le terrain (a ou a `CDaoFieldExchange::param`).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération actuelle est appropriée pour le type de champ mis à jour.

### <a name="remarks"></a>Notes

Certaines des opérations effectuées par le mécanisme DFX ne s’appliquent qu’à l’un des types de terrain possibles. Suivez le modèle des fonctions DFX existantes.

Pour plus d’informations sur l’écriture de routines DFX personnalisées, voir [Note technique 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDaoFieldExchange::m_nOperation

Identifie l’opération à effectuer sur l’objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) associé à l’objet d’échange de champ.

### <a name="remarks"></a>Notes

L’objet `CDaoFieldExchange` fournit le contexte d’un certain nombre d’opérations DFX différentes sur le dossier.

> [!NOTE]
> La valeur PSEUDONULL décrite dans les opérations MarkForAddNew et SetFieldNull ci-dessous est une valeur utilisée pour marquer les champs Null. Le mécanisme d’échange de terrain d’enregistrement DAO (DFX) utilise cette valeur pour déterminer quels champs ont été explicitement marqués Null. PSEUDONULL n’est pas nécessaire pour les champs [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) et [COleCurrency.](../../mfc/reference/colecurrency-class.md)

Les valeurs `m_nOperation` possibles sont les :

|Opération|Description|
|---------------|-----------------|
|`AddToParameterList`|Construit la clause **PARAMETERS** de la déclaration SQL.|
|`AddToSelectList`|Construit la clause **SELECT** de la déclaration SQL.|
|`BindField`|Lie un champ dans la base de données à un emplacement de mémoire dans votre application.|
|`BindParam`|Définit les valeurs de paramètres pour la requête du recordet.|
|`Fixup`|Définit le statut Null pour un champ.|
|`AllocCache`|Alloue le cache utilisé pour vérifier les champs "sales" dans le jeu d’enregistrement.|
|`StoreField`|Enregistre l’enregistrement actuel dans le cache.|
|`LoadField`|Restaure les variables des membres de données mises en cache dans l’enregistrement.|
|`FreeCache`|Libère le cache utilisé pour vérifier les champs "sales" dans le jeu d’enregistrement.|
|`SetFieldNull`|Définit le statut d’un champ à Null et la valeur de PSEUDONULL.|
|`MarkForAddNew`|Marque les champs "sale" sinon PSEUDONULL.|
|`MarkForEdit`|Marques champs "sale" s’ils ne correspondent pas à la cache.|
|`SetDirtyField`|Définit les valeurs de champ marquées comme « sales ».|
|`DumpField`|Déverse le contenu d’un champ (déboguer uniquement).|
|`MaxDFXOperation`|Utilisé pour la vérification des entrées.|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDaoFieldExchange::m_prs

Contient un pointeur sur l’objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) associé à l’objet. `CDaoFieldExchange`

### <a name="remarks"></a>Notes

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType

Appelez `SetFieldType` la `CDaoRecordset` dérogation de `DoFieldExchange` votre classe.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Paramètres

*nFieldType (en)*<br/>
Une valeur de **l’enum FieldType**, déclaré en `CDaoFieldExchange`, qui peut être l’un des suivants:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Notes

Normalement, ClassWizard écrit cet appel pour vous. Si vous écrivez votre propre fonction et `DoFieldExchange` utilisez l’assistant pour écrire votre fonction, ajoutez des appels à votre propre fonction en dehors de la carte de champ. Si vous n’utilisez pas l’assistant, il n’y aura pas de carte de terrain. L’appel précède les appels vers les fonctions DFX, un pour chaque membre `CDaoFieldExchange::outputColumn`des données de champ de votre classe, et identifie le type de champ comme .

Si vous paramétisez votre classe de nombres d’enregistrements, vous devez ajouter des appels DFX pour tous les membres de données de paramètres (en dehors de la carte de champ) et précéder ces appels par un appel à `SetFieldType`. Passer la `CDaoFieldExchange::param`valeur . (Vous pouvez, au lieu de cela, utiliser un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) et définir ses valeurs de paramètres.)

En général, chaque groupe d’appels de fonction DFX associés aux membres de `SetFieldType`données sur le terrain ou aux données de paramètres membres doit être précédé d’un appel à . Le paramètre *nFieldType* de chaque `SetFieldType` appel identifie le type de données représentées `SetFieldType` par les appels de fonction DFX qui suivent l’appel.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
