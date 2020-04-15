---
title: Classe COleDateTimeSpan
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
ms.openlocfilehash: 7173fa0b6261ea718a02d399d944a1b5bb98b9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317739"
---
# <a name="coledatetimespan-class"></a>Classe COleDateTimeSpan

Représente un temps relatif, une durée.

## <a name="syntax"></a>Syntaxe

```
class COleDateTimeSpan
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COledateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Construit un objet `COleDateTimeSpan`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|Génère une représentation de chaîne `COleDateTimeSpan` formatée d’un objet.|
|[COleDateTimeSpan::GetDays](#getdays)|Retourne la partie de `COleDateTimeSpan` jour de la travée que représente cet objet.|
|[COleDateTimeSpan::GetHours](#gethours)|Retourne la partie d’heure de la travée que représente cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::GetMinutes](#getminutes)|Retourne la partie minute `COleDateTimeSpan` de la travée que représente cet objet.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Retourne la deuxième partie `COleDateTimeSpan` de la travée que représente cet objet.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Obtient le statut (validité) de cet `COleDateTimeSpan` objet.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Retourne le nombre `COleDateTimeSpan` de jours que cet objet représente.|
|[COledateTimeSpan::GetTotalHours](#gettotalhours)|Retourne le nombre `COleDateTimeSpan` d’heures que cet objet représente.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Retourne le nombre `COleDateTimeSpan` de minutes que cet objet représente.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Retourne le nombre `COleDateTimeSpan` de secondes que cet objet représente.|
|[COledateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Définit la valeur `COleDateTimeSpan` de cet objet.|
|[COledateTimeSpan::SetStatus](#setstatus)|Définit l’état (validité) de cet `COleDateTimeSpan` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|||
|-|-|
|[opérateur, -](#operator_add_-)|Ajouter, soustraire et `COleDateTimeSpan` changer de signe pour les valeurs.|
|[opérateur , --](#operator_add_eq_-_eq)|Ajoutez et soustrayez une `COleDateTimeSpan` valeur de cette `COleDateTimeSpan` valeur.|
|[opérateur](#operator_eq)|Copie `COleDateTimeSpan` d’une valeur.|
|[l’opérateur, <, <](#coledatetimespan_relational_operators)|Comparez `COleDateTimeSpan` deux valeurs.|
|[double (opérateur)](#operator_double)|Convertit `COleDateTimeSpan` cette valeur en un **double**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Contient le **double** `COleDateTimeSpan` sous-jacent pour cet objet.|
|[COleDateTimeSpan::m_status](#m_status)|Contient l’état `COleDateTimeSpan` de cet objet.|

## <a name="remarks"></a>Notes

`COleDateTimeSpan`n’a pas de classe de base.

Un `COleDateTimeSpan` garde du temps en quelques jours.

`COleDateTimeSpan`est utilisé avec sa classe compagnon [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime`encapsule le `DATE` type de données de l’automatisation OLE. `COleDateTime`représente des valeurs de temps absolues. Tous `COleDateTime` les `COleDateTimeSpan` calculs impliquent des valeurs. La relation entre ces classes est analogue à celle entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Pour plus d’informations sur les `COleDateTime` cours et `COleDateTimeSpan` les cours, voir l’article Date et [heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Spécifications

**En-tête:** ATLComTime.h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>Opérateurs relationnels COleDateTimeSpan

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

Ces opérateurs comparent deux valeurs de date/temps-span et retournent VRAI si la condition est vraie ; autrement FALSE.

### <a name="remarks"></a>Notes

> [!NOTE]
> Un ATLASSERT se produira si l’un ou l’autre opérande est invalide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COledateTimeSpan::COleDateTimeSpan

Construit un objet `COleDateTimeSpan`.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Paramètres

*dblSpanSrc*<br/>
Nombre de jours à copier dans `COleDateTimeSpan` le nouvel objet.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Indiquez les valeurs de jour et `COleDateTimeSpan` d’heure à copier dans le nouvel objet.

### <a name="remarks"></a>Notes

Tous ces constructeurs `COleDateTimeSpan` créent de nouveaux objets paraspécifisés à la valeur spécifiée. Voici une brève description de chacun de ces constructeurs :

- **COleDateTimeSpan( )** Construit un `COleDateTimeSpan` objet initialisé à 0.

- **COleDateTimeSpan(** `dblSpanSrc` **)** Construit un `COleDateTimeSpan` objet à partir d’une valeur de point flottant.

- **COleDateTimeSpan(** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** Construit un `COleDateTimeSpan` objet para initialisé aux valeurs numériques spécifiées.

L’état du `COleDateTimeSpan` nouvel objet est défini comme valide.

Pour plus d’informations `COleDateTimeSpan` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan::Format

Génère une représentation de chaîne `COleDateTimeSpan` formatée d’un objet.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*pFormat (en)*<br/>
Une chaîne de formatage similaire à la `printf` chaîne de formatage. Les codes de formatage,`%`précédés d’un signe `COleDateTimeSpan` en pourcentage, sont remplacés par le composant correspondant. D’autres caractères de la chaîne de formatage sont copiés inchangés à la chaîne retournée. La valeur et la signification `Format` des codes de formatage pour sont énumérés ci-dessous:

- **%H** Heures dans la journée actuelle

- **%M** Procès-verbal dans l’heure actuelle

- **%S** Secondes dans la minute actuelle

- **%%** Signe de pourcentage

Les quatre codes de format énumérés ci-dessus sont les seuls codes que Format acceptera.

-

*nID*<br/>
L’ID de ressource pour la chaîne de contrôle du format.

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient la date formatée / valeur de durée.

### <a name="remarks"></a>Notes

Appelez ces fonctions pour créer une représentation formatée de la valeur de durée. Si l’état `COleDateTimeSpan` de cet objet est nul, la valeur de retour est une chaîne vide. Si le statut est invalide, la chaîne de retour est spécifiée par la ressource de chaîne IDS_INVALID_DATETIMESPAN.

Voici une brève description des formulaires de cette fonction :

**Format(** *pFormat* **)**<br/>
Ce formulaire formate la valeur à l’aide de la chaîne de format qui `printf`contient des codes de formatage spéciaux qui sont précédés d’un signe de pourcentage (%), comme dans . La chaîne de formatage est passée comme un paramètre de la fonction.

**Format(** *nID* **)**<br/>
Ce formulaire formate la valeur à l’aide de la chaîne de format qui `printf`contient des codes de formatage spéciaux qui sont précédés d’un signe de pourcentage (%), comme dans . La chaîne de formatage est une ressource. L’ID de cette ressource de chaîne est passé comme paramètre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays

Récupère la partie de jour de cette date/durée de la valeur.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Valeur de retour

La partie de jour de cette date/durée de la valeur.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre environ - 3 615 000 et 3 615 000.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetHours](#gethours)

- [GetMinutes GetMinutes](#getminutes)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan::GetHours

Récupère la partie horaire de cette date/durée de la valeur.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

La partie heures de cette date/durée de la valeur.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre - 23 et 23.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetMinutes GetMinutes](#getminutes)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan::GetMinutes

Récupère la partie minute de cette date/durée de la valeur.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

La partie minutes de cette date/durée de la valeur.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre - 59 et 59.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetHours](#gethours)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan::GetSeconds

Récupère la deuxième partie de cette date/durée de la valeur.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

La partie secondes de cette date/durée de la valeur.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre - 59 et 59.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetHours](#gethours)

- [GetMinutes GetMinutes](#getminutes)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan::GetStatus

Obtient le statut (validité) de cet `COleDateTimeSpan` objet.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valeur de retour

L’état `COleDateTimeSpan` de cette valeur.

### <a name="remarks"></a>Notes

La valeur de rendement `DateTimeSpanStatus` est définie par le type `COleDateTimeSpan` énuméré, qui est défini au sein de la classe.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Pour une brève description de ces valeurs de statut, consultez la liste suivante :

- `COleDateTimeSpan::valid`Indique que `COleDateTimeSpan` cet objet est valide.

- `COleDateTimeSpan::invalid`Indique que `COleDateTimeSpan` cet objet est invalide; c’est-à-dire que sa valeur peut être incorrecte.

- `COleDateTimeSpan::null`Indique que `COleDateTimeSpan` cet objet est nul, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « nul » dans le sens de base de données de « n’avoir aucune valeur », par opposition au NULL DE C.)

L’état `COleDateTimeSpan` d’un objet est invalide dans les cas suivants :

- Si cet objet a subi un débordement ou un sous-flux `+=` au `-=`cours d’une opération d’affectation arithmétique, à savoir, ou .

- Si une valeur invalide a été attribuée à cet objet.

- Si l’état de cet objet `SetStatus`a été explicitement mis à invalider en utilisant .

Pour plus d’informations sur les opérations qui peuvent mettre le statut à invalide, voir [COleDateTimeSpan::opérateur , -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) et [COleDateTimeSpan::opérateur ' - -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Pour plus d’informations `COleDateTimeSpan` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

Récupère cette date/durée de la valeur exprimée en jours.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date/durée exprimée en jours. Bien que cette fonction soit prototype pour retourner un double, elle retournera toujours une valeur integer.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre environ - 3.65e6 et 3.65e6.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetHours](#gethours)

- [GetMinutes GetMinutes](#getminutes)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COledateTimeSpan::GetTotalHours

Récupère cette date/durée de la valeur exprimée en heures.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date/durée exprimée en heures. Bien que cette fonction soit prototype pour retourner un double, elle retournera toujours une valeur integer.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre environ - 8.77e7 et 8.77e7.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetHours](#gethours)

- [GetMinutes GetMinutes](#getminutes)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

Voir l’exemple pour [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes

Récupère cette date/durée de la valeur exprimée en quelques minutes.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date/durée exprimée en quelques minutes. Bien que cette fonction soit prototype pour retourner un double, elle retournera toujours une valeur integer.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre environ - 5.26e9 et 5.26e9.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetHours](#gethours)

- [GetMinutes GetMinutes](#getminutes)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

Voir l’exemple pour [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds

Récupère cette date/durée de la valeur exprimée en quelques secondes.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

Cette valeur de date/durée s’exprime en quelques secondes. Bien que cette fonction soit prototype pour retourner un double, elle retournera toujours une valeur integer.

### <a name="remarks"></a>Notes

Les valeurs de retour de cette fonction varient entre environ - 3.16e11 à 3.16e11.

Pour d’autres fonctions qui `COleDateTimeSpan` interrogent la valeur d’un objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetHours](#gethours)

- [GetMinutes GetMinutes](#getminutes)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Exemple

Voir l’exemple pour [GetTotalDays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan::m_span

La **double** valeur `COleDateTime` sous-jacente de cet objet.

```
double m_span;
```

### <a name="remarks"></a>Notes

Cette valeur exprime la date/durée en jours.

> [!CAUTION]
> Changer la valeur **du** double membre de `COleDateTimeSpan` données modifiera la valeur de cet objet. Il ne change pas `COleDateTimeSpan` l’état de cet objet.

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan::m_status

Le type pour ce membre de `DateTimeSpanStatus`données est le `COleDateTimeSpan` type énuméré , qui est défini dans la classe.

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

Pour une brève description de ces valeurs de statut, consultez la liste suivante :

- `COleDateTimeSpan::valid`Indique que `COleDateTimeSpan` cet objet est valide.

- `COleDateTimeSpan::invalid`Indique que `COleDateTimeSpan` cet objet est invalide; c’est-à-dire que sa valeur peut être incorrecte.

- `COleDateTimeSpan::null`Indique que `COleDateTimeSpan` cet objet est nul, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « nul » dans le sens de base de données de « n’avoir aucune valeur », par opposition au NULL DE C.)

L’état `COleDateTimeSpan` d’un objet est invalide dans les cas suivants :

- Si cet objet a subi un débordement ou un sous-flux `+=` au `-=`cours d’une opération d’affectation arithmétique, à savoir, ou .

- Si une valeur invalide a été attribuée à cet objet.

- Si l’état de cet objet a été explicitement mis à invalider à l’aide [de SetStatus](#setstatus).

Pour plus d’informations sur les opérations qui peuvent mettre le statut à invalide, voir [COleDateTimeSpan::opérateur , -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) et [COleDateTimeSpan::opérateur ' - -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Ce membre des données est destiné à des situations de programmation avancées. Vous devez utiliser les fonctions de membre en ligne [GetStatus](#getstatus) et [SetStatus](#setstatus). Voir `SetStatus` pour d’autres mises en garde concernant le réglage explicite de ce membre des données.

Pour plus d’informations `COleDateTimeSpan` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan::opérateur

Copie `COleDateTimeSpan` d’une valeur.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Notes

Cet opérateur d’affectation surchargé copie la date de `COleDateTimeSpan` source/durée de la valeur dans cet objet.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan::opérateur, -

Ajouter, soustraire et `COleDateTimeSpan` changer de signe pour les valeurs.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Notes

Les deux premiers opérateurs vous permettent d’ajouter et de soustraire les valeurs de date/temps. Le troisième vous permet de modifier le signe d’une valeur de date/temps.

Si l’un ou l’autre des opérandes est nul, l’état de la valeur résultante `COleDateTimeSpan` est nul.

Si l’un ou l’autre des opérandes est invalide et que l’autre n’est pas nul, le statut de la valeur résultante `COleDateTimeSpan` est invalide.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::opérateur ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '

Ajoutez et soustrayez une `COleDateTimeSpan` valeur de cette `COleDateTimeSpan` valeur.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de `COleDateTimeSpan` soustraire les valeurs de date/temps de cet objet. Si l’un ou l’autre des opérandes est nul, l’état de la valeur résultante `COleDateTimeSpan` est nul.

Si l’un ou l’autre des opérandes est invalide et que l’autre n’est pas nul, le statut de la valeur résultante `COleDateTimeSpan` est invalide.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan::opérateur double

Convertit `COleDateTimeSpan` cette valeur en un **double**.

```
operator double() const throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne la `COleDateTimeSpan` valeur de cette valeur comme un nombre de points flottants de jours.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COledateTimeSpan::SetDateTimeSpan

Définit la valeur de cette date/durée de la valeur.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Paramètres

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Indiquer les valeurs de date et de durée `COleDateTimeSpan` à copier dans cet objet.

### <a name="remarks"></a>Notes

Pour les fonctions qui interrogent la valeur d’un `COleDateTimeSpan` objet, voir les fonctions suivantes du membre :

- [GetDays (en)](#getdays)

- [GetHours](#gethours)

- [GetMinutes GetMinutes](#getminutes)

- [GetSeconds GetSeconds](#getseconds)

- [GetTotalDays (en)](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds (en)](#gettotalseconds)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COledateTimeSpan::SetStatus

Définit l’état (validité) de cet `COleDateTimeSpan` objet.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
La nouvelle valeur `COleDateTimeSpan` de statut pour cet objet.

### <a name="remarks"></a>Notes

La valeur *du paramètre de statut* est définie par le `DateTimeSpanStatus` type énuméré, qui est défini au sein de la `COleDateTimeSpan` classe.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Pour une brève description de ces valeurs de statut, consultez la liste suivante :

- `COleDateTimeSpan::valid`Indique que `COleDateTimeSpan` cet objet est valide.

- `COleDateTimeSpan::invalid`Indique que `COleDateTimeSpan` cet objet est invalide; c’est-à-dire que sa valeur peut être incorrecte.

- `COleDateTimeSpan::null`Indique que `COleDateTimeSpan` cet objet est nul, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « nul » dans le sens de base de données de « n’avoir aucune valeur », par opposition au NULL DE C.)

   > [!CAUTION]
   > Cette fonction est pour les situations de programmation avancées. Cette fonction ne modifie pas les données de cet objet. Il sera le plus souvent utilisé pour définir le statut à **null ou** **invalide**. Notez que l’opérateur[d’affectation (opérateur](#operator_eq)) et [SetDateTimeSpan](#setdatetimespan) définissons l’état de l’objet en fonction de la valeur source.s).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[Classe CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[Classe CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
