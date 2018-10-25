---
title: COleDateTimeSpan, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e50fe341ff52916d16b3c006e438fe2bfa99154
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082838"
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
|[COleDateTimeSpan::Format](#format)|Génère une représentation sous forme de chaîne mise en forme d’un `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::GetDays](#getdays)|Retourne la partie jour de l’étendue de cette `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::GetHours](#gethours)|Retourne la partie heure de l’étendue de cette `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::GetMinutes](#getminutes)|Retourne la partie minute de l’étendue de cette `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Retourne la deuxième partie de l’étendue de cette `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Obtient l’état (validité) de ce `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Retourne le nombre de jours pendant lesquels ce `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Retourne le nombre d’heures cette `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Retourne le nombre de minutes cela `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Retourne le nombre de secondes pendant lesquelles cela `COleDateTimeSpan` représente l’objet.|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Définit la valeur de cette `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::SetStatus](#setstatus)|Définit l’état (validité) de ce `COleDateTimeSpan` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|||
|-|-|
|[opérateur +, -](#operator_add_-)|Ajouter, soustraire et modifier l’authentification pour `COleDateTimeSpan` valeurs.|
|[opérateur +=, =](#operator_add_eq_-_eq)|Ajouter ou soustraire un `COleDateTimeSpan` valeur à partir de ce `COleDateTimeSpan` valeur.|
|[opérateur =](#operator_eq)|Copie un `COleDateTimeSpan` valeur.|
|[opérateur ==, <, < =](#coledatetimespan_relational_operators)|Comparer deux `COleDateTimeSpan` valeurs.|
|[double (opérateur)](#operator_double)|Convertit cette `COleDateTimeSpan` valeur un **double**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Contient sous-jacent **double** pour ce `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::m_status](#m_status)|Contient l’état de ce `COleDateTimeSpan` objet.|

## <a name="remarks"></a>Notes

`COleDateTimeSpan` n’a pas d’une classe de base.

Un `COleDateTimeSpan` conserve la durée en jours.

`COleDateTimeSpan` est utilisé avec sa classe compagnon [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime` encapsule le `DATE` type de données d’OLE automation. `COleDateTime` représente les valeurs de temps absolues. Tous les `COleDateTime` impliquent des calculs `COleDateTimeSpan` valeurs. La relation entre ces classes est analogue à celle entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Pour plus d’informations sur la `COleDateTime` et `COleDateTimeSpan` classes, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** ATLComTime.h

##  <a name="coledatetimespan_relational_operators"></a>  Opérateurs relationnels COleDateTimeSpan

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

### <a name="return-value"></a>Valeur de retour

Ces opérateurs comparent deux valeurs de date/heure-étendue et retourne la valeur TRUE si la condition est true ; Sinon, FALSE.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Un ATLASSERT ; se produit si des opérandes ne sont pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

##  <a name="coledatetimespan"></a>  COleDateTimeSpan::COleDateTimeSpan

Construit un objet `COleDateTimeSpan`.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Paramètres

*dblSpanSrc*<br/>
Le nombre de jours doit être copié dans le nouveau `COleDateTimeSpan` objet.

*lDays*, *nHours*, *nMins*, *every*<br/>
Indiquer les valeurs de jour et d’heure doit être copié dans le nouveau `COleDateTimeSpan` objet.

### <a name="remarks"></a>Notes

Toutes ces constructeurs créent `COleDateTimeSpan` objets initialisés à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit :

- **() COleDateTimeSpan** construit un `COleDateTimeSpan` objet initialisé à 0.

- **COleDateTimeSpan (** `dblSpanSrc` **)** construit un `COleDateTimeSpan` objet à partir d’une valeur à virgule flottante.

- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)**  Construit un `COleDateTimeSpan` objet initialisé avec les valeurs numériques spécifiées.

L’état de la nouvelle `COleDateTimeSpan` objet est défini à valide.

Pour plus d’informations sur les limites de `COleDateTimeSpan` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

##  <a name="format"></a>  COleDateTimeSpan::Format

Génère une représentation sous forme de chaîne mise en forme d’un `COleDateTimeSpan` objet.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*pFormat*<br/>
Une mise en forme de chaîne similaire à la `printf` mise en forme de chaîne. Mise en forme de codes, précédés d’un pourcentage (`%`) vous connecter, sont remplacés par le correspondantes `COleDateTimeSpan` composant. Autres caractères dans la chaîne mise en forme sont copiées sans modification à la chaîne retournée. La valeur et la signification des codes de mise en forme pour `Format` sont répertoriées ci-dessous :

- **%H** heures du jour actuel

- **%M** minutes à l’heure actuelle

- **%S** secondes dans la minute actuelle

- **%%** Signe de pourcentage

Les codes de format quatre répertoriées ci-dessus sont les codes de Format acceptera uniquement.

-

*nID*<br/>
L’ID de ressource pour la chaîne de format de contrôle.

### <a name="return-value"></a>Valeur de retour

Un `CString` qui contient la valeur de date/heure-intervalle de mise en forme.

### <a name="remarks"></a>Notes

Appeler ces fonctions pour créer une représentation sous forme de mise en forme de la valeur d’intervalle de temps. Si l’état de ce `COleDateTimeSpan` objet est null, la valeur de retour est une chaîne vide. Si l’état n’est pas valide, la chaîne de retour est spécifiée par la ressource de chaîne IDS_INVALID_DATETIMESPAN.

Une brève description des formes pour cette fonction suit :

**Format (** *pFormat* **)**<br/>
Ce formulaire met en forme la valeur à l’aide de la chaîne de format qui contient les codes de mise en forme spéciales qui sont précédés d’un signe de pourcentage (%), comme dans `printf`. La chaîne mise en forme est passée en tant que paramètre à la fonction.

**Format (** *nID* **)**<br/>
Ce formulaire met en forme la valeur à l’aide de la chaîne de format qui contient les codes de mise en forme spéciales qui sont précédés d’un signe de pourcentage (%), comme dans `printf`. La chaîne mise en forme est une ressource. L’ID de ressource de cette chaîne est passée comme paramètre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

##  <a name="getdays"></a>  COleDateTimeSpan::GetDays

Récupère la partie jour de cette valeur de date /-intervalle de temps.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Valeur de retour

La partie jour de cette valeur de date /-intervalle de temps.

### <a name="remarks"></a>Notes

La valeur de retour des valeurs à partir de cette plage de fonction entre environ - 3,615,000 et 3,615,000.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

##  <a name="gethours"></a>  COleDateTimeSpan::GetHours

Récupère la partie de cette valeur de période date/heure.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

Les heures de cette valeur de date /-intervalle de temps.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonction entre - 23 et 23.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

##  <a name="getminutes"></a>  COleDateTimeSpan::GetMinutes

Récupère la partie minute de cette valeur de date /-intervalle de temps.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

La partie minutes de cette valeur de date /-intervalle de temps.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonction entre - 59 et 59.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

##  <a name="getseconds"></a>  COleDateTimeSpan::GetSeconds

Récupère la deuxième partie de cette valeur de date /-intervalle de temps.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

La partie secondes de cette valeur de date /-intervalle de temps.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonction entre - 59 et 59.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

##  <a name="getstatus"></a>  COleDateTimeSpan::GetStatus

Obtient l’état (validité) de ce `COleDateTimeSpan` objet.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valeur de retour

L’état de ce `COleDateTimeSpan` valeur.

### <a name="remarks"></a>Notes

La valeur de retour est définie par le `DateTimeSpanStatus` type énuméré, qui est défini dans le `COleDateTimeSpan` classe.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :

- `COleDateTimeSpan::valid` Indique que ce `COleDateTimeSpan` objet est valide.

- `COleDateTimeSpan::invalid` Indique que ce `COleDateTimeSpan` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleDateTimeSpan::null` Indique que ce `COleDateTimeSpan` objet a la valeur null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « null » dans le sens de la base de données de « ne having aucune valeur, », par opposition à la valeur NULL en C++.)

L’état d’un `COleDateTimeSpan` objet n’est pas valide dans les cas suivants :

- Si cet objet a rencontré un dépassement de capacité positif ou négatif pendant une opération arithmétique d’assignation, à savoir, `+=` ou `-=`.

- Si une valeur non valide a été affectée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non valide à l’aide de `SetStatus`.

Pour plus d’informations sur les opérations qui peuvent définir l’état comme étant non valide, consultez [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) et [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Pour plus d’informations sur les limites de `COleDateTimeSpan` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="gettotaldays"></a>  COleDateTimeSpan::GetTotalDays

Récupère cette valeur de date /-intervalle de temps exprimée en jours.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date /-intervalle de temps exprimée en jours. Bien que cette fonction est prototypée pour retourner une valeur double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonction entre environ - 3.65e6 et 3.65e6.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

##  <a name="gettotalhours"></a>  COleDateTimeSpan::GetTotalHours

Récupère cette valeur de date /-intervalle de temps exprimée en heures.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date /-intervalle de temps exprimée en heures. Bien que cette fonction est prototypée pour retourner une valeur double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonction entre environ - 8.77e7 et 8.77e7.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

Consultez l’exemple de [GetTotalDays](#gettotaldays).

##  <a name="gettotalminutes"></a>  COleDateTimeSpan::GetTotalMinutes

Récupère cette valeur de date /-intervalle de temps exprimée en minutes.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date /-intervalle de temps exprimée en minutes. Bien que cette fonction est prototypée pour retourner une valeur double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette plage de fonction entre environ - 5.26e9 et 5.26e9.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Exemple

Consultez l’exemple de [GetTotalDays](#gettotaldays).

##  <a name="gettotalseconds"></a>  COleDateTimeSpan::GetTotalSeconds

Récupère cette valeur de date /-intervalle de temps exprimée en secondes.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date /-intervalle de temps exprimée en secondes. Bien que cette fonction est prototypée pour retourner une valeur double, elle retourne toujours une valeur entière.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction est comprise entre environ - 3.16e11 à 3.16e11.

Pour les autres fonctions interroger la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Exemple

Consultez l’exemple de [GetTotalDays](#gettotaldays).

##  <a name="m_span"></a>  COleDateTimeSpan::m_span

Sous-jacent **double** valeur pour ce `COleDateTime` objet.

```
double m_span;
```

### <a name="remarks"></a>Notes

Cette valeur exprime la date /-intervalle de temps en jours.

> [!CAUTION]
>  Modification de la valeur dans le **double** membre de données changera la valeur de cette `COleDateTimeSpan` objet. Il ne modifie pas l’état de ce `COleDateTimeSpan` objet.

##  <a name="m_status"></a>  COleDateTimeSpan::m_status

Le type de ce membre de données est le type énuméré `DateTimeSpanStatus`, qui est défini dans le `COleDateTimeSpan` classe.

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

Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :

- `COleDateTimeSpan::valid` Indique que ce `COleDateTimeSpan` objet est valide.

- `COleDateTimeSpan::invalid` Indique que ce `COleDateTimeSpan` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleDateTimeSpan::null` Indique que ce `COleDateTimeSpan` objet a la valeur null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « null » dans le sens de la base de données de « ne having aucune valeur, », par opposition à la valeur NULL en C++.)

L’état d’un `COleDateTimeSpan` objet n’est pas valide dans les cas suivants :

- Si cet objet a rencontré un dépassement de capacité positif ou négatif pendant une opération arithmétique d’assignation, à savoir, `+=` ou `-=`.

- Si une valeur non valide a été affectée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non valide à l’aide de [SetStatus](#setstatus).

Pour plus d’informations sur les opérations qui peuvent définir l’état comme étant non valide, consultez [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) et [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
>  Ce membre de données concerne les situations de programmation avancées. Vous devez utiliser les fonctions de membre inline [GetStatus](#getstatus) et [SetStatus](#setstatus). Consultez `SetStatus` pour des précautions supplémentaires concernant la définition explicite de ce membre de données.

Pour plus d’informations sur les limites de `COleDateTimeSpan` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_eq"></a>  COleDateTimeSpan::operator =

Copie un `COleDateTimeSpan` valeur.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Notes

Cet opérateur d’assignation surchargés copie la valeur de date/heure-étendue de source dans cette `COleDateTimeSpan` objet.

##  <a name="operator_add_-"></a>  COleDateTimeSpan::operator +, -

Ajouter, soustraire et modifier l’authentification pour `COleDateTimeSpan` valeurs.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Notes

Les deux premiers opérateurs vous permettent d’ajouter et de soustraire les valeurs de date /-intervalle de temps. Le troisième vous permet de modifier le signe d’une valeur de date /-intervalle de temps.

Si un des opérandes est null, l’état des résultats de `COleDateTimeSpan` la valeur est null.

Si un des opérandes n’est pas valide et que l’autre n’est pas null, l’état des résultats de `COleDateTimeSpan` valeur n’est pas valide.

Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTimeSpan::operator +=, =

Ajouter ou soustraire un `COleDateTimeSpan` valeur à partir de ce `COleDateTimeSpan` valeur.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire les valeurs de date /-intervalle de temps à partir de ce `COleDateTimeSpan` objet. Si un des opérandes est null, l’état des résultats de `COleDateTimeSpan` la valeur est null.

Si un des opérandes n’est pas valide et que l’autre n’est pas null, l’état des résultats de `COleDateTimeSpan` valeur n’est pas valide.

Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

##  <a name="operator_double"></a>  COleDateTimeSpan::operator double

Convertit cette `COleDateTimeSpan` valeur un **double**.

```
operator double() const throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne la valeur de cette `COleDateTimeSpan` valeur sous la forme d’un nombre à virgule flottante de jours.

##  <a name="setdatetimespan"></a>  COleDateTimeSpan::SetDateTimeSpan

Définit la valeur de cette valeur de date /-intervalle de temps.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Paramètres

*lDays*, *nHours*, *nMins*, *every*<br/>
Indiquer les valeurs de plage de dates et d’intervalle de temps doit être copié dans ce `COleDateTimeSpan` objet.

### <a name="remarks"></a>Notes

Pour les fonctions qui interrogent la valeur d’un `COleDateTimeSpan` d’objets, consultez les fonctions membres suivantes :

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

##  <a name="setstatus"></a>  COleDateTimeSpan::SetStatus

Définit l’état (validité) de ce `COleDateTimeSpan` objet.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Paramètres

*status*<br/>
La nouvelle valeur d’état pour ce `COleDateTimeSpan` objet.

### <a name="remarks"></a>Notes

Le *état* valeur du paramètre est définie par le `DateTimeSpanStatus` type énuméré, qui est défini dans le `COleDateTimeSpan` classe.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :

- `COleDateTimeSpan::valid` Indique que ce `COleDateTimeSpan` objet est valide.

- `COleDateTimeSpan::invalid` Indique que ce `COleDateTimeSpan` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleDateTimeSpan::null` Indique que ce `COleDateTimeSpan` objet a la valeur null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « null » dans le sens de la base de données de « ne having aucune valeur, », par opposition à la valeur NULL en C++.)

   > [!CAUTION]
   > Cette fonction concerne les situations de programmation avancées. Cette fonction ne modifie pas les données dans cet objet. Il sera plus souvent utilisée pour définir l’état sur **null** ou **non valide**. Notez que l’opérateur d’assignation ( [opérateur =](#eq)) et [SetDateTimeSpan](#setdatetimespan) ne définissez pas l’état de l’objet basé sur la valeur (s) source.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[COleDateTime, classe](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime, classe](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan, classe](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

