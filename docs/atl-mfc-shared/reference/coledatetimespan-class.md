---
description: 'En savoir plus sur : classe COleDateTimeSpan'
title: COleDateTimeSpan, classe
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 51632f8c179ea0e256c39052e924d296b89aefd0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166770"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan, classe

Représente une heure relative, un intervalle de temps.

## <a name="syntax"></a>Syntaxe

```
class COleDateTimeSpan
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Construit un objet `COleDateTimeSpan`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDateTimeSpan :: format](#format)|Génère une représentation sous forme de chaîne mise en forme d’un `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::GetDays](#getdays)|Retourne la partie jour de l’étendue représentée par cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan :: GetHours](#gethours)|Retourne la partie heure de l’étendue représentée par cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan :: GetMinutes](#getminutes)|Retourne la partie minute de l’étendue représentée par cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan :: GetSeconds](#getseconds)|Retourne la deuxième partie de l’étendue représentée par cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan :: GetStatus](#getstatus)|Obtient l’État (validité) de cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Retourne le nombre de jours que cet `COleDateTimeSpan` objet représente.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Retourne le nombre d’heures que cet `COleDateTimeSpan` objet représente.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Retourne le nombre de minutes que cet `COleDateTimeSpan` objet représente.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Retourne le nombre de secondes que cet `COleDateTimeSpan` objet représente.|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Définit la valeur de cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan :: SetStatus](#setstatus)|Définit l’État (validité) de cet `COleDateTimeSpan` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|-|-|
|[opérateur +,-](#operator_add_-)|Ajouter, soustraire et modifier le signe des `COleDateTimeSpan` valeurs.|
|[opérateur + =,-=](#operator_add_eq_-_eq)|Ajouter et soustraire une `COleDateTimeSpan` valeur de cette `COleDateTimeSpan` valeur.|
|[opérateur =](#operator_eq)|Copie une `COleDateTimeSpan` valeur.|
|[opérateur = =, <, <=](#coledatetimespan_relational_operators)|Compare deux `COleDateTimeSpan` valeurs.|
|[double, opérateur](#operator_double)|Convertit cette `COleDateTimeSpan` valeur en **`double`** .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDateTimeSpan :: m_span](#m_span)|Contient le sous-jacent **`double`** pour cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan :: m_status](#m_status)|Contient l’état de cet `COleDateTimeSpan` objet.|

## <a name="remarks"></a>Notes

`COleDateTimeSpan` n’a pas de classe de base.

Une `COleDateTimeSpan` durée de conservation en jours.

`COleDateTimeSpan` est utilisé avec sa classe complémentaire [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime` encapsule le `DATE` type de données d’OLE Automation. `COleDateTime` représente les valeurs d’heure absolues. Tous les `COleDateTime` calculs impliquent des `COleDateTimeSpan` valeurs. La relation entre ces classes est analogue à celle entre [ctime](../../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Pour plus d’informations sur `COleDateTime` les `COleDateTimeSpan` classes et, consultez l’article [date et heure : prise en charge d’Automation](../date-and-time.md).

## <a name="requirements"></a>Spécifications

**En-tête :** ATLComTime. h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a> COleDateTimeSpan, opérateurs relationnels

Opérateurs de comparaison.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>Paramètres

*dateSpan*<br/>
`COleDateTimeSpan` à comparer.

### <a name="return-value"></a>Valeur renvoyée

Ces opérateurs comparent deux valeurs Date/Time-span et retournent TRUE si la condition est true ; Sinon, FALSe.

### <a name="remarks"></a>Notes

> [!NOTE]
> Un ATLASSERT se produit si l’un des opérandes n’est pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a> COleDateTimeSpan::COleDateTimeSpan

Construit un objet `COleDateTimeSpan`.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Paramètres

*dblSpanSrc*<br/>
Nombre de jours à copier dans le nouvel `COleDateTimeSpan` objet.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Indique les valeurs de date et d’heure à copier dans le nouvel `COleDateTimeSpan` objet.

### <a name="remarks"></a>Notes

Tous ces constructeurs créent des `COleDateTimeSpan` objets initialisés à la valeur spécifiée. Voici une brève description de chacun de ces constructeurs :

- **COleDateTimeSpan ()** Construit un `COleDateTimeSpan` objet initialisé à 0.

- **COleDateTimeSpan (** `dblSpanSrc` **)** construit un `COleDateTimeSpan` objet à partir d’une valeur à virgule flottante.

- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** construit un `COleDateTimeSpan` objet initialisé aux valeurs numériques spécifiées.

L’état du nouvel `COleDateTimeSpan` objet est défini sur valide.

Pour plus d’informations sur les limites des `COleDateTimeSpan` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../date-and-time.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a> COleDateTimeSpan :: format

Génère une représentation sous forme de chaîne mise en forme d’un `COleDateTimeSpan` objet.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*pFormat*<br/>
Chaîne de mise en forme similaire à la `printf` chaîne de mise en forme. Les codes de mise en forme, précédés d’un signe de pourcentage ( `%` ), sont remplacés par le `COleDateTimeSpan` composant correspondant. Les autres caractères de la chaîne de mise en forme sont copiés sans modification dans la chaîne retournée. La valeur et la signification des codes de mise en forme pour `Format` sont répertoriées ci-dessous :

- **% H** Heures du jour en cours

- **% M** Minutes dans l’heure actuelle

- **% S** Secondes dans la minute actuelle

- **%%** Signe de pourcentage

Les quatre codes de format répertoriés ci-dessus sont les seuls codes acceptés par le format.

-

*nID*<br/>
ID de ressource pour la chaîne de contrôle de format.

### <a name="return-value"></a>Valeur renvoyée

`CString`Qui contient la valeur de date/heure de mise en forme.

### <a name="remarks"></a>Notes

Appelez ces fonctions pour créer une représentation mise en forme de la valeur d’intervalle de temps. Si l’état de cet `COleDateTimeSpan` objet est null, la valeur de retour est une chaîne vide. Si l’État n’est pas valide, la chaîne de retour est spécifiée par la IDS_INVALID_DATETIMESPAN de ressource de type chaîne.

Une brève description des formulaires pour cette fonction est la suivante :

**Format (** *pFormat* **)**<br/>
Cette forme met en forme la valeur à l’aide de la chaîne de format qui contient des codes de mise en forme spéciaux précédés d’un signe de pourcentage (%), comme dans `printf` . La chaîne de mise en forme est transmise en tant que paramètre à la fonction.

**Format (** *nid* **)**<br/>
Cette forme met en forme la valeur à l’aide de la chaîne de format qui contient des codes de mise en forme spéciaux précédés d’un signe de pourcentage (%), comme dans `printf` . La chaîne de mise en forme est une ressource. L’ID de cette ressource de type chaîne est passé en tant que paramètre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a> COleDateTimeSpan::GetDays

Récupère la partie jour de cette valeur de date/heure.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

La partie jour de cette valeur de date/d’heure.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonctions sont comprises entre-3 615 000 et 3 615 000.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a> COleDateTimeSpan :: GetHours

Récupère la partie heure de cette valeur de date/heure.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

La partie heures de cette valeur de date/heure.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonctions sont comprises entre-23 et 23.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a> COleDateTimeSpan :: GetMinutes

Récupère la partie minute de cette valeur de date/heure.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

La partie minutes de cette valeur date/heure-span.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonctions sont comprises entre-59 et 59.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a> COleDateTimeSpan :: GetSeconds

Récupère la deuxième partie de cette valeur de date/heure.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

La partie secondes de cette valeur de date/d’heure.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonctions sont comprises entre-59 et 59.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a> COleDateTimeSpan :: GetStatus

Obtient l’État (validité) de cet `COleDateTimeSpan` objet.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

État de cette `COleDateTimeSpan` valeur.

### <a name="remarks"></a>Notes

La valeur de retour est définie par le `DateTimeSpanStatus` type énuméré, qui est défini dans la `COleDateTimeSpan` classe.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante :

- `COleDateTimeSpan::valid` Indique que cet `COleDateTimeSpan` objet est valide.

- `COleDateTimeSpan::invalid` Indique que cet `COleDateTimeSpan` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleDateTimeSpan::null` Indique que cet `COleDateTimeSpan` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « NULL » dans le sens de la base de données « n’ayant aucune valeur », par opposition à la valeur NULL C++.)

L’état d’un `COleDateTimeSpan` objet n’est pas valide dans les cas suivants :

- Si cet objet a rencontré un dépassement de capacité positif ou négatif au cours d’une opération d’assignation arithmétique, à savoir `+=` ou `-=` .

- Si une valeur non valide a été assignée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non valide à l’aide de `SetStatus` .

Pour plus d’informations sur les opérations qui peuvent définir l’État sur non valide, consultez [COleDateTimeSpan :: Operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) et [COleDateTimeSpan :: Operator + =,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Pour plus d’informations sur les limites des `COleDateTimeSpan` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../date-and-time.md).

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a> COleDateTimeSpan::GetTotalDays

Récupère cette valeur de date/heure exprimée en jours.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Cette valeur de date/heure est exprimée en jours. Bien que cette fonction soit prototypée pour retourner une valeur de type double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction sont comprises entre-3.65 E6 et 3.65 E6.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a> COleDateTimeSpan::GetTotalHours

Récupère cette valeur de date/heure exprimée en heures.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Cette valeur de date/heure est exprimée en heures. Bien que cette fonction soit prototypée pour retourner une valeur de type double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction sont comprises entre-8.77 E7 et 8.77 E7.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a> COleDateTimeSpan::GetTotalMinutes

Récupère cette valeur de date/heure exprimée en minutes.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Cette valeur de date/heure est exprimée en minutes. Bien que cette fonction soit prototypée pour retourner une valeur de type double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction sont comprises entre 5.26 E9 et 5.26 E9.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a> COleDateTimeSpan::GetTotalSeconds

Récupère cette valeur de date/heure exprimée en secondes.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Cette valeur de date/heure est exprimée en secondes. Bien que cette fonction soit prototypée pour retourner une valeur de type double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction sont comprises entre-3.16 E11 et 3.16 E11.

Pour les autres fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetTotalDays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a> COleDateTimeSpan :: m_span

Valeur sous-jacente **`double`** de cet `COleDateTime` objet.

```
double m_span;
```

### <a name="remarks"></a>Notes

Cette valeur exprime l’intervalle de date/heure en jours.

> [!CAUTION]
> La modification de la valeur dans le **`double`** membre de données modifie la valeur de cet `COleDateTimeSpan` objet. Elle ne modifie pas l’état de cet `COleDateTimeSpan` objet.

## <a name="coledatetimespanm_status"></a><a name="m_status"></a> COleDateTimeSpan :: m_status

Le type de ce membre de données est le type énuméré `DateTimeSpanStatus` , qui est défini dans la `COleDateTimeSpan` classe.

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>Notes

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante :

- `COleDateTimeSpan::valid` Indique que cet `COleDateTimeSpan` objet est valide.

- `COleDateTimeSpan::invalid` Indique que cet `COleDateTimeSpan` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleDateTimeSpan::null` Indique que cet `COleDateTimeSpan` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « NULL » dans le sens de la base de données « n’ayant aucune valeur », par opposition à la valeur NULL C++.)

L’état d’un `COleDateTimeSpan` objet n’est pas valide dans les cas suivants :

- Si cet objet a rencontré un dépassement de capacité positif ou négatif au cours d’une opération d’assignation arithmétique, à savoir `+=` ou `-=` .

- Si une valeur non valide a été assignée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non valide à l’aide d' [SetStatus](#setstatus).

Pour plus d’informations sur les opérations qui peuvent définir l’État sur non valide, consultez [COleDateTimeSpan :: Operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) et [COleDateTimeSpan :: Operator + =,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Ce membre de données est destiné à des situations de programmation avancées. Vous devez utiliser les fonctions membres inline [GetStatus](#getstatus) et [SetStatus](#setstatus). `SetStatus`Pour plus d’informations sur la définition explicite de ce membre de données, consultez.

Pour plus d’informations sur les limites des `COleDateTimeSpan` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../date-and-time.md).

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a> COleDateTimeSpan :: Operator =

Copie une `COleDateTimeSpan` valeur.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Notes

Cet opérateur d’assignation surchargé copie la valeur de date/heure de la source dans cet `COleDateTimeSpan` objet.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a> COleDateTimeSpan :: Operator +,-

Ajouter, soustraire et modifier le signe des `COleDateTimeSpan` valeurs.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Notes

Les deux premiers opérateurs vous permettent d’ajouter et de soustraire des valeurs de date/d’heure. La troisième vous permet de modifier le signe d’une valeur de date/d’heure.

Si l’un des opérandes est null, l’état de la valeur résultante `COleDateTimeSpan` est null.

Si l’un des opérandes n’est pas valide et que l’autre n’est pas null, l’état de la valeur résultante `COleDateTimeSpan` n’est pas valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> COleDateTimeSpan :: Operator + =,-=

Ajouter et soustraire une `COleDateTimeSpan` valeur de cette `COleDateTimeSpan` valeur.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire des valeurs de date/heure de cet `COleDateTimeSpan` objet. Si l’un des opérandes est null, l’état de la valeur résultante `COleDateTimeSpan` est null.

Si l’un des opérandes n’est pas valide et que l’autre n’est pas null, l’état de la valeur résultante `COleDateTimeSpan` n’est pas valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a> COleDateTimeSpan :: Operator double

Convertit cette `COleDateTimeSpan` valeur en **`double`** .

```
operator double() const throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne la valeur de cette `COleDateTimeSpan` valeur sous la forme d’un nombre de jours à virgule flottante.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a> COleDateTimeSpan::SetDateTimeSpan

Définit la valeur de cette valeur de date/heure.

```cpp
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Paramètres

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Indiquez les valeurs de date et d’intervalle de dates à copier dans cet `COleDateTimeSpan` objet.

### <a name="remarks"></a>Notes

Pour les fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a> COleDateTimeSpan :: SetStatus

Définit l’État (validité) de cet `COleDateTimeSpan` objet.

```cpp
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Nouvelle valeur d’État pour cet `COleDateTimeSpan` objet.

### <a name="remarks"></a>Notes

La valeur du paramètre *Status* est définie par le `DateTimeSpanStatus` type énuméré, qui est défini dans la `COleDateTimeSpan` classe.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante :

- `COleDateTimeSpan::valid` Indique que cet `COleDateTimeSpan` objet est valide.

- `COleDateTimeSpan::invalid` Indique que cet `COleDateTimeSpan` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleDateTimeSpan::null` Indique que cet `COleDateTimeSpan` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « NULL » dans le sens de la base de données « n’ayant aucune valeur », par opposition à la valeur NULL C++.)

   > [!CAUTION]
   > Cette fonction est destinée à des situations de programmation avancées. Cette fonction ne modifie pas les données de cet objet. Le plus souvent, il est utilisé pour définir l’État sur **null** ou **non valide**. Notez que l’opérateur d’assignation ([Operator =](#operator_eq)) et [SetDateTimeSpan](#setdatetimespan) définissent l’état de l’objet en fonction de la ou des valeurs sources.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[COleDateTime (classe)](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[Classe CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan, classe](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
