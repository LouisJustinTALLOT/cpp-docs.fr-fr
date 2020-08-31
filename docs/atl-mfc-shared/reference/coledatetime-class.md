---
title: COleDateTime (classe)
description: Référence d’API pour la classe MFC COleDateTime qui encapsule le `DATE` type de données utilisé dans OLE Automation.
ms.date: 08/27/2020
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 9ebbab02860daaeb57c24d3e0901666861adfc2b
ms.sourcegitcommit: c8f1605354724a13566bc3b0fac3c5d98265f1d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062156"
---
# <a name="coledatetime-class"></a>COleDateTime (classe)

Encapsule le `DATE` type de données utilisé dans OLE Automation.

## <a name="syntax"></a>Syntaxe

```
class COleDateTime
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime :: COleDateTime](#coledatetime)|Construit un objet `COleDateTime`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDateTime :: format](#format)|Génère une représentation sous forme de chaîne mise en forme d’un `COleDateTime` objet.|
|[COleDateTime :: GetAsDBTIMESTAMP](#getasdbtimestamp)|Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la forme d’une `DBTIMESTAMP` structure de données.|
|[COleDateTime :: GetAsSystemTime](#getassystemtime)|Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la forme d’une structure de données [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .|
|[COleDateTime :: GetAsUDATE](#getasudate)|Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` en tant que `UDATE` structure de données.|
|[COleDateTime :: GetCurrentTime](#getcurrenttime)|Crée un `COleDateTime` objet qui représente l’heure actuelle (fonction membre statique).|
|[COleDateTime :: GetDay](#getday)|Retourne le jour représenté par cet `COleDateTime` objet (1-31).|
|[COleDateTime :: GetDayOfWeek](#getdayofweek)|Retourne le jour de la semaine représenté par cet `COleDateTime` objet (dimanche = 1).|
|[COleDateTime :: GetDayOfYear](#getdayofyear)|Retourne le jour de l’année représenté par cet `COleDateTime` objet (1er janvier = 1).|
|[COleDateTime :: GetHour](#gethour)|Retourne l’heure représentée par cet `COleDateTime` objet (0-23).|
|[COleDateTime :: GetMinute](#getminute)|Retourne la minute que cet `COleDateTime` objet représente (0-59).|
|[COleDateTime :: GetMonth](#getmonth)|Retourne le mois représenté par cet `COleDateTime` objet (1-12).|
|[COleDateTime :: GetSecond](#getsecond)|Retourne le deuxième représenté par cet `COleDateTime` objet (0-59).|
|[COleDateTime :: GetStatus](#getstatus)|Obtient l’État (validité) de cet `COleDateTime` objet.|
|[COleDateTime :: GetYear](#getyear)|Retourne l’année représentée par cet `COleDateTime` objet.|
|[COleDateTime ::P arseDateTime](#parsedatetime)|Lit une valeur de date/heure à partir d’une chaîne et définit la valeur de `COleDateTime` .|
|[COleDateTime :: SetDate](#setdate)|Affecte à la valeur de cet `COleDateTime` objet la valeur de date uniquement spécifiée.|
|[COleDateTime :: SetDateTime](#setdatetime)|Affecte la valeur de `COleDateTime` date/heure spécifiée à cet objet.|
|[COleDateTime :: SetStatus](#setstatus)|Définit l’État (validité) de cet `COleDateTime` objet.|
|[COleDateTime :: SetTime](#settime)|Définit la valeur de cet `COleDateTime` objet à la valeur d’heure spécifiée uniquement.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime :: Operator = =, COleDateTime :: opérateur <, etc.](#coledatetime_relational_operators)|Compare deux `COleDateTime` valeurs.|
|[COleDateTime :: Operator +, COleDateTime :: Operator-](#operator_add_-)|Ajouter et soustraire des `COleDateTime` valeurs.|
|[COleDateTime :: Operator + =, COleDateTime :: opérateur-=](#operator_add_eq_-_eq)|Ajouter et soustraire une `COleDateTime` valeur de cet `COleDateTime` objet.|
|[COleDateTime :: Operator =](#operator_eq)|Copie une `COleDateTime` valeur.|
|[COleDateTime :: Operator DATE, COleDateTime :: Operator date *](#operator_date)|Convertit une `COleDateTime` valeur en `DATE` ou `DATE*` .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime :: m_dt](#m_dt)|Contient le sous-jacent `DATE` pour cet `COleDateTime` objet.|
|[COleDateTime :: m_status](#m_status)|Contient l’état de cet `COleDateTime` objet.|

## <a name="remarks"></a>Remarques

`COleDateTime` n’a pas de classe de base.

Il s’agit de l’un des types possibles pour le type de données [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) de OLE Automation. Une `COleDateTime` valeur représente une valeur de date et d’heure absolue.

Le `DATE` type est implémenté en tant que valeur à virgule flottante. Les jours sont mesurés à partir du 30 décembre 1899, à minuit. Le tableau suivant présente certaines dates et leurs valeurs associées :

|Date|Value|
|----------|-----------|
|29 décembre 1899, minuit|-1.0|
|29 décembre 1899, 6 A. M|-1.25|
|30 décembre 1899, minuit|0,0|
|31 décembre 1899, minuit|1.0|
|1er janvier, de 1900 à 18:00|2.25|

> [!CAUTION]
> Dans le tableau ci-dessus, bien que les valeurs de jour deviennent négatives avant minuit le 30 décembre 1899, les valeurs d’heure de la journée ne le sont pas. Par exemple, 6:00 AM est toujours représenté par une valeur fractionnaire 0,25 que l’entier représentant le jour soit positif (après le 30 décembre 1899) ou négatif (avant le 30 décembre 1899). Cela signifie qu’une simple comparaison de virgule flottante trie par erreur un `COleDateTime` représentant 6:00 AM sur 12/29/1899, en **plus** d’une comparaison représentant 7:00 AM le même jour.

La `COleDateTime` classe gère les dates comprises entre le 1er janvier 100 et le 31 décembre 9999. La `COleDateTime` classe utilise le calendrier grégorien ; elle ne prend pas en charge les dates juliennes. `COleDateTime` ignore l’heure d’été. (Voir [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Vous pouvez utiliser le `%y` format pour récupérer une année sur deux chiffres uniquement pour les dates commençant à 1900. Si vous utilisez le `%y` format à une date antérieure à 1900, le code génère un échec d’assertion.

Ce type est également utilisé pour représenter des valeurs de date ou d’heure uniquement. Par Convention, la date 0 (30 décembre 1899) est utilisée pour les valeurs de temps uniquement et l’heure 00:00 (minuit) est utilisée pour les valeurs de date uniquement.

Si vous créez un `COleDateTime` objet à l’aide d’une date antérieure à 100, la date est acceptée, mais les appels suivants à `GetYear` , `GetMonth` , `GetDay` , `GetHour` , `GetMinute` et `GetSecond` échouent et retournent-1. Auparavant, vous pouviez utiliser des dates à deux chiffres, mais les dates doivent être 100 ou supérieures dans MFC 4,2 et versions ultérieures.

Pour éviter les problèmes, spécifiez une date à quatre chiffres. Par exemple :

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Les opérations arithmétiques de base pour les `COleDateTime` valeurs utilisent la classe complémentaire [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan` les valeurs définissent un intervalle de temps. La relation entre ces classes est semblable à celle entre [ctime](../../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Pour plus d’informations sur `COleDateTime` les `COleDateTimeSpan` classes et, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** ATLComTime. h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a> Opérateurs relationnels COleDateTime

Opérateurs de comparaison.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>Paramètres

*date*<br/>
Objet `COleDateTime` à comparer.

### <a name="remarks"></a>Remarques

> [!NOTE]
> Un ATLASSERT se produit si l’un des deux opérandes n’est pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Exemple

Les opérateurs **>=** , **\<=**, **>** et **<** déclarent si l' `COleDateTime` objet a la valeur null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a> COleDateTime :: COleDateTime

Construit un objet `COleDateTime`.

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>Paramètres

*dateSrc*<br/>
Objet existant `COleDateTime` à copier dans le nouvel `COleDateTime` objet.

*varSrc*<br/>
`VARIANT`Structure de données existante (éventuellement un `COleVariant` objet) à convertir en valeur de date/heure (VT_DATE) et copiée dans le nouvel `COleDateTime` objet.

*dtSrc*<br/>
Valeur de date/heure ( `DATE` ) à copier dans le nouvel `COleDateTime` objet.

*timeSrc*<br/>
`time_t`Valeur ou `__time64_t` à convertir en valeur de date/heure et copiées dans le nouvel `COleDateTime` objet.

*systimeSrc*<br/>
`SYSTEMTIME`Structure à convertir en valeur de date/heure et copiée dans le nouvel `COleDateTime` objet.

*filetimeSrc*<br/>
`FILETIME`Structure à convertir en valeur de date/heure et copiée dans le nouvel `COleDateTime` objet. Un `FILETIME` utilise le temps universel coordonné (UTC, Universal Coordinated Time). par conséquent, si vous transmettez une heure locale dans la structure, vos résultats sont incorrects. Pour plus d’informations, consultez [temps de fichier](/windows/win32/SysInfo/file-times) dans le SDK Windows.

*nYear*, *nMonth*, *nJour*, *nheure*, *nMin*, *nSec*<br/>
Indiquez les valeurs de date et d’heure à copier dans le nouvel `COleDateTime` objet.

*wDosDate*, *wDosTime*<br/>
Valeurs de date et d’heure MS-DOS à convertir en valeur de date/heure et copiées dans le nouvel `COleDateTime` objet.

*Confirmé*<br/>
Référence à une structure [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) contenant l’heure locale actuelle.

### <a name="remarks"></a>Remarques

Tous ces constructeurs créent des `COleDateTime` objets initialisés à la valeur spécifiée. Le tableau suivant indique les plages valides pour chaque composant de date et d’heure :

|Composant de date/heure|Plage valide|
|--------------------------|-----------------|
|year|100-9999|
|month|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

Notez que la limite supérieure réelle pour le composant jour varie en fonction des composants mois et année. Pour plus d’informations, consultez les `SetDate` `SetDateTime` fonctions membres ou.

Vous trouverez ci-dessous une brève description de chaque constructeur :

- `COleDateTime(`**)** Construit un `COleDateTime` objet initialisé à 0 (minuit, 30 décembre 1899).

- `COleDateTime(``dateSrc` **)** Construit un `COleDateTime` objet à partir d’un `COleDateTime` objet existant.

- `COleDateTime(`*varSrc* **)** construit un `COleDateTime` objet. Tente de convertir un `VARIANT` objet structure ou [COleVariant](../../mfc/reference/colevariant-class.md) en valeur date/heure ( `VT_DATE` ). Si cette conversion réussit, la valeur convertie est copiée dans le nouvel `COleDateTime` objet. Si ce n’est pas le cas, la valeur de l' `COleDateTime` objet est définie sur 0 (minuit, 30 décembre 1899) et son état sur non valide.

- `COleDateTime(``dtSrc` **)** Construit un `COleDateTime` objet à partir d’une `DATE` valeur.

- `COleDateTime(``timeSrc` **)** Construit un `COleDateTime` objet à partir d’une `time_t` valeur.

- `COleDateTime(`*systimeSrc* **)** construit un `COleDateTime` objet à partir d’une `SYSTEMTIME` valeur.

- `COleDateTime(``filetimeSrc` **)** Construit un `COleDateTime` objet à partir d’une `FILETIME` valeur. . Un `FILETIME` utilise le temps universel coordonné (UTC, Universal Coordinated Time). par conséquent, si vous transmettez une heure locale dans la structure, vos résultats sont incorrects. Pour plus d’informations, consultez [temps de fichier](/windows/win32/SysInfo/file-times) dans le SDK Windows.

- `COleDateTime(``nYear`, `nMonth` , `nDay` , `nHour` , `nMin` , `nSec` **)** Construit un `COleDateTime` objet à partir des valeurs numériques spécifiées.

- `COleDateTime(``wDosDate`, `wDosTime` **)** Construit un `COleDateTime` objet à partir des valeurs de date et d’heure ms-dos spécifiées.

Pour plus d’informations sur le `time_t` type de données, consultez la fonction [Time](../../c-runtime-library/reference/time-time32-time64.md) dans la référence de la *bibliothèque*Runtime.

Pour plus d’informations, consultez les structures [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows.

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> Le constructeur qui utilise le `DBTIMESTAMP` paramètre n’est disponible que lorsque OleDb. h est inclus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a> COleDateTime :: format

Crée une représentation mise en forme de la valeur de date/heure.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indique l’un des indicateurs de paramètres régionaux suivants :

- LOCALE_NOUSEROVERRIDE utiliser les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.

- VAR_TIMEVALUEONLY ignorer la partie de date pendant l’analyse.

- VAR_DATEVALUEONLY ignorer la partie heure pendant l’analyse.

*lcid*<br/>
Indique l’ID de paramètres régionaux à utiliser pour la conversion. Pour plus d’informations sur les identificateurs de langue, consultez [identificateurs de langue](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Chaîne de mise en forme similaire à la `printf` chaîne de mise en forme. Chaque code de mise en forme, précédé d’un signe de pourcentage ( `%` ), est remplacé par le `COleDateTime` composant correspondant. Les autres caractères de la chaîne de mise en forme sont copiés sans modification dans la chaîne retournée. Pour plus d’informations, consultez la fonction runtime [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). La valeur et la signification des codes de mise en forme pour `Format` sont les suivantes :

- `%H` Heures du jour en cours

- `%M` Minutes dans l’heure actuelle

- `%S` Secondes dans la minute actuelle

- `%%` Signe de pourcentage

*nFormatID*<br/>
ID de ressource pour la chaîne de contrôle de format.

### <a name="return-value"></a>Valeur de retour

`CString`Qui contient la valeur de date/heure mise en forme.

### <a name="remarks"></a>Remarques

Si l’état de cet `COleDateTime` objet est null, la valeur de retour est une chaîne vide. Si l’État n’est pas valide, la chaîne de retour est spécifiée par la ATL_IDS_DATETIME_INVALID de ressource de type chaîne.

Une brève description des trois formes pour cette fonction est la suivante :

`Format`( *dwFlags*, *LCID*)<br/>
Cette forme met en forme la valeur à l’aide des spécifications de langue (ID de paramètres régionaux) pour la date et l’heure. À l’aide des paramètres par défaut, ce formulaire affiche la date et l’heure, sauf si la partie heure a la valeur 0 (minuit), auquel cas il n’imprimera que la date, ou la partie date est 0 (30 décembre 1899), auquel cas il imprimera uniquement le temps. Si la valeur de date/heure est 0 (30 décembre 1899, minuit), cette forme avec les paramètres par défaut s’imprimera à minuit.

`Format`( *lpszFormat*)<br/>
Cette forme met en forme la valeur à l’aide de la chaîne de format qui contient des codes de mise en forme spéciaux précédés d’un signe de pourcentage (%), comme dans `printf` . La chaîne de mise en forme est transmise en tant que paramètre à la fonction. Pour plus d’informations sur les codes de mise en forme, consultez [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans la référence de la bibliothèque Runtime.

`Format`( *nFormatID*)<br/>
Cette forme met en forme la valeur à l’aide de la chaîne de format qui contient des codes de mise en forme spéciaux précédés d’un signe de pourcentage (%), comme dans `printf` . La chaîne de mise en forme est une ressource. L’ID de cette ressource de type chaîne est passé en tant que paramètre. Pour plus d’informations sur les codes de mise en forme, consultez [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans la référence de la *bibliothèque Runtime*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a> COleDateTime :: GetAsDBTIMESTAMP

Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la forme d’une `DBTIMESTAMP` structure de données.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Paramètres

*Confirmé*<br/>
Référence à une structure [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) .

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Remarques

Stocke l’heure résultante dans la structure d' *horodatage* référencée. La `DBTIMESTAMP` structure de données initialisée par cette fonction aura son `fraction` membre défini sur zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a> COleDateTime :: GetAsSystemTime

Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la forme d’une `SYSTEMTIME` structure de données.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Paramètres

*sysTime*<br/>
Référence à une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir la valeur de date/heure convertie de l' `COleDateTime` objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite ; FALSe si la conversion échoue, ou si l' `COleDateTime` objet est null ou non valide.

### <a name="remarks"></a>Remarques

`GetAsSystemTime` stocke l’heure résultante dans l’objet *sysTime* référencé. La `SYSTEMTIME` structure de données initialisée par cette fonction aura son `wMilliseconds` membre défini sur zéro.

Pour plus d’informations sur les informations d’État contenues dans un `COleDateTime` objet, consultez [GetStatus](#getstatus).

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a> COleDateTime :: GetAsUDATE

Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la forme d’une `UDATE` structure de données.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Paramètres

*uDate*<br/>
Référence à une `UDATE` structure pour recevoir la valeur de date/heure convertie de l' `COleDateTime` objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite ; FALSe si la conversion échoue, ou si l' `COleDateTime` objet est null ou non valide.

### <a name="remarks"></a>Remarques

Une `UDATE` structure représente une date « décompressée ».

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a> COleDateTime :: GetCurrentTime

Appelez cette fonction membre statique pour retourner la valeur de date/heure actuelle.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a> COleDateTime :: GetDay

Obtient le jour du mois représenté par cette valeur de date/heure.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valeur de retour

Jour du mois représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour n’a pas pu être obtenu.

### <a name="remarks"></a>Remarques

La plage des valeurs de retour valides est comprise entre 1 et 31.

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a> COleDateTime :: GetDayOfWeek

Obtient le jour de la semaine représenté par cette valeur de date/heure.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valeur de retour

Jour de la semaine représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour de la semaine n’a pas pu être obtenu.

### <a name="remarks"></a>Remarques

La plage des valeurs de retour valides est comprise entre 1 et 7, où 1 = dimanche, 2 = lundi, et ainsi de suite.

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a> COleDateTime :: GetDayOfYear

Obtient le jour de l’année représenté par cette valeur de date/heure.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Valeur de retour

Jour de l’année représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour de l’année n’a pas pu être obtenu.

### <a name="remarks"></a>Remarques

La plage des valeurs de retour valides est comprise entre 1 et 366, où 1 janvier = 1.

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a> COleDateTime :: GetHour

Obtient l’heure représentée par cette valeur de date/heure.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valeur de retour

L’heure représentée par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si l’heure n’a pas pu être obtenue.

### <a name="remarks"></a>Remarques

La plage des valeurs de retour valides est comprise entre 0 et 23.

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a> COleDateTime :: GetMinute

Obtient la minute représentée par cette valeur de date/heure.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valeur de retour

Minute représentée par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si la minute n’a pas pu être obtenue.

### <a name="remarks"></a>Remarques

La plage des valeurs de retour valides est comprise entre 0 et 59.

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetHour](#gethour).

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a> COleDateTime :: GetMonth

Obtient le mois représenté par cette valeur de date/heure.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valeur de retour

Mois représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le mois n’a pas pu être obtenu.

### <a name="remarks"></a>Remarques

La plage des valeurs de retour valides est comprise entre 1 et 12.

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

Consultez l’exemple pour [getDay](#getday).

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a> COleDateTime :: GetSecond

Obtient le deuxième représenté par cette valeur de date/heure.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valeur de retour

Deuxième représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le deuxième n’a pas pu être obtenu.

### <a name="remarks"></a>Remarques

La plage des valeurs de retour valides est comprise entre 0 et 59.

> [!NOTE]
> La `COleDateTime` classe ne prend pas en charge les secondes bissextiles.

Pour plus d’informations sur l’implémentation de `COleDateTime` , consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetHour](#gethour).

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a> COleDateTime :: GetStatus

Obtient l’État (validité) d’un `COleDateTime` objet donné.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’état de cette `COleDateTime` valeur. Si vous appelez `GetStatus` sur un `COleDateTime` objet construit avec la valeur par défaut, il retourne la valeur valide. Si vous appelez `GetStatus` sur un `COleDateTime` objet initialisé avec le constructeur ayant la valeur null, `GetStatus` retourne la valeur null.

### <a name="remarks"></a>Remarques

La valeur de retour est définie par le `DateTimeStatus` type énuméré, qui est défini dans la `COleDateTime` classe.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante :

- `COleDateTime::error` Indique qu’une erreur s’est produite lors de la tentative d’obtention d’une partie de la valeur de date/heure.

- `COleDateTime::valid` Indique que cet `COleDateTime` objet est valide.

- `COleDateTime::invalid` Indique que cet `COleDateTime` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.

- `COleDateTime::null` Indique que cet `COleDateTime` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « NULL » dans le sens de la base de données « n’ayant aucune valeur », par opposition à la valeur NULL C++.)

L’état d’un `COleDateTime` objet n’est pas valide dans les cas suivants :

- Si sa valeur est définie à partir d’une `VARIANT` `COleVariant` valeur ou qui n’a pas pu être convertie en valeur de date/heure.

- Si sa valeur est définie à partir d’une `time_t` `SYSTEMTIME` valeur, ou `FILETIME` qui n’a pas pu être convertie en valeur de date/heure valide.

- Si sa valeur est définie par `SetDateTime` avec des valeurs de paramètre non valides.

- Si cet objet a rencontré un dépassement de capacité positif ou négatif au cours d’une opération d’assignation arithmétique, à savoir `+=` ou `-=` .

- Si une valeur non valide a été assignée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non valide à l’aide de `SetStatus` .

Pour plus d’informations sur les opérations qui peuvent affecter la valeur non valide à l’État, consultez les fonctions membres suivantes :

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [opérateur +,-](#operator_add_-)

- [opérateur + =,-=](#operator_add_eq_-_eq)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a> COleDateTime :: GetYear

Obtient l’année représentée par cette valeur de date/heure.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Valeur de retour

Année représentée par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si l’année n’a pas pu être obtenue.

### <a name="remarks"></a>Remarques

Les valeurs de retour valides sont comprises entre 100 et 9999, ce qui comprend le siècle.

Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

Consultez l’exemple pour [getDay](#getday).

## <a name="coledatetimem_dt"></a><a name="m_dt"></a> COleDateTime :: m_dt

Structure sous-jacente `DATE` de cet `COleDateTime` objet.

```
DATE m_dt;
```

### <a name="remarks"></a>Remarques

> [!CAUTION]
> La modification de la valeur dans l' `DATE` objet accessible par le pointeur retourné par cette fonction modifie la valeur de cet `COleDateTime` objet. Elle ne modifie pas l’état de cet `COleDateTime` objet.

Pour plus d’informations sur l’implémentation de l' `DATE` objet, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimem_status"></a><a name="m_status"></a> COleDateTime :: m_status

Contient l’état de cet `COleDateTime` objet.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Remarques

Le type de ce membre de données est le type énuméré `DateTimeStatus` , qui est défini dans la `COleDateTime` classe. Pour plus d’informations, consultez [COleDateTime :: GetStatus](#getstatus).

> [!CAUTION]
> Ce membre de données est destiné à des situations de programmation avancées. Vous devez utiliser les fonctions membres inline [GetStatus](#getstatus) et [SetStatus](#setstatus). `SetStatus`Pour plus d’informations sur la définition explicite de ce membre de données, consultez.

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a> COleDateTime :: Operator =

Copie une `COleDateTime` valeur.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Remarques

Ces opérateurs d’assignation surchargés copient la valeur de date/heure source dans cet `COleDateTime` objet. Une brève description de chaque opérateur d’assignation surchargé est la suivante :

- **Operator = (** `dateSrc` **)** la valeur et l’état de l’opérande sont copiés dans cet `COleDateTime` objet.

- **opérateur = (** *varSrc* **)** Si la conversion de la valeur [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) (ou de l’objet [COleVariant](../../mfc/reference/colevariant-class.md) ) en date/heure (VT_DATE) réussit, la valeur convertie est copiée dans cet `COleDateTime` objet et son état est défini sur valide. Si la conversion échoue, la valeur de cet objet est définie à zéro (30 décembre 1899, minuit) et son état est non valide.

- **Operator = (** `dtSrc` **)** la `DATE` valeur est copiée dans cet `COleDateTime` objet et son état est défini sur valide.

- **Operator = (** `timeSrc` **)** la `time_t` `__time64_t` valeur ou est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide ; en cas d’échec, la valeur est non valide.

- **opérateur = (** *systimeSrc* **)** La valeur [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide ; en cas d’échec, la valeur est non valide.

- **Operator = (** `uDate` **)** la `UDATE` valeur est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide ; en cas d’échec, la valeur est non valide. Une `UDATE` structure représente une date « décompressée ». Pour plus d’informations, consultez la fonction [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **Operator = (** `filetimeSrc` **)** la valeur [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide ; Sinon, elle a la valeur non valide. `FILETIME` utilise le temps universel coordonné (UTC, Universal Coordinated Time). par conséquent, si vous transmettez une heure UTC dans la structure, vos résultats sont convertis de l’heure UTC en heure locale et sont stockés sous forme de temps variant. Ce comportement est le même que dans Visual C++ 6,0 et Visual C++ .NET 2003 SP2. Pour plus d’informations, consultez [temps de fichier](/windows/win32/SysInfo/file-times) dans le SDK Windows.

Pour plus d’informations, consultez l’entrée [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) dans la SDK Windows.

Pour plus d’informations sur le `time_t` type de données, consultez la fonction [Time](../../c-runtime-library/reference/time-time32-time64.md) dans la référence de la *bibliothèque*Runtime.

Pour plus d’informations, consultez les structures [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows.

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a> COleDateTime :: Operator +,-

Ajouter et soustraire des `ColeDateTime` valeurs.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Remarques

`COleDateTime` les objets représentent des heures absolues. Les objets [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) représentent les heures relatives. Les deux premiers opérateurs vous permettent d’ajouter et de soustraire une `COleDateTimeSpan` valeur d’une `COleDateTime` valeur. Le troisième opérateur vous permet de soustraire une `COleDateTime` valeur d’une autre pour produire une `COleDateTimeSpan` valeur.

Si l’un des opérandes est null, l’état de la valeur résultante `COleDateTime` est null.

Si la valeur résultante `COleDateTime` se trouve en dehors des limites des valeurs acceptables, l’état de cette `COleDateTime` valeur n’est pas valide.

Si l’un des opérandes n’est pas valide et que l’autre n’est pas null, l’état de la valeur résultante `COleDateTime` n’est pas valide.

Les **+** **-** opérateurs et déclarent si l' `COleDateTime` objet a la valeur null. Pour obtenir un exemple, consultez la rubrique relative aux [opérateurs relationnels COleDateTime](#coledatetime_relational_operators) .

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a> COleDateTime :: Operator + =,-=

Ajouter et soustraire une `ColeDateTime` valeur de cet `COleDateTime` objet.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Remarques

Ces opérateurs vous permettent d’ajouter et de soustraire une `COleDateTimeSpan` valeur à ce `COleDateTime` . Si l’un des opérandes est null, l’état de la valeur résultante `COleDateTime` est null.

Si la valeur résultante `COleDateTime` se trouve en dehors des limites des valeurs acceptables, l’état de cette `COleDateTime` valeur est défini sur non valide.

Si l’un des opérandes n’est pas valide et que l’autre n’est pas null, l’état de la valeur résultante `COleDateTime` n’est pas valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

Les **+=** **-=** opérateurs et déclarent si l' `COleDateTime` objet a la valeur null. Pour obtenir un exemple, consultez la rubrique relative aux [opérateurs relationnels COleDateTime](#coledatetime_relational_operators) .

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a> COleDateTime :: Operator DATE

Convertit une `ColeDateTime` valeur en `DATE` .

```
operator DATE() const throw();
```

### <a name="remarks"></a>Remarques

Cet opérateur retourne un `DATE` objet dont la valeur est copiée à partir de cet `COleDateTime` objet. Pour plus d’informations sur l’implémentation de l' `DATE` objet, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

L' `DATE` opérateur déclare si l' `COleDateTime` objet a la valeur null. Pour obtenir un exemple, consultez la rubrique relative aux [opérateurs relationnels COleDateTime](#coledatetime_relational_operators) .

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a> COleDateTime ::P arseDateTime

Analyse une chaîne pour lire une valeur de date/heure.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Paramètres

*lpszDate*<br/>
Pointeur vers la chaîne terminée par le caractère null qui doit être analysée. Pour plus d'informations, consultez Notes.

*dwFlags*<br/>
Indique des indicateurs pour les paramètres régionaux et l’analyse. Un ou plusieurs des indicateurs suivants :

- LOCALE_NOUSEROVERRIDE utiliser les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.

- VAR_TIMEVALUEONLY ignorer la partie de date pendant l’analyse.

- VAR_DATEVALUEONLY ignorer la partie heure pendant l’analyse.

*lcid*<br/>
Indique l’ID de paramètres régionaux à utiliser pour la conversion.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la chaîne a été correctement convertie en valeur de date/heure ; sinon, FALSe.

### <a name="remarks"></a>Remarques

Si la chaîne a été correctement convertie en valeur de date/heure, la valeur de cet `COleDateTime` objet est définie sur cette valeur et son état sur valide.

> [!NOTE]
> Les valeurs d’année doivent être comprises entre 100 et 9999, inclus.

Le paramètre *lpszDate* peut prendre plusieurs formats. Par exemple, les chaînes suivantes contiennent des formats de date/heure acceptables :

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

L’ID de paramètres régionaux détermine également si le format de chaîne est acceptable pour la conversion en une valeur de date/heure.

Dans le cas de VAR_DATEVALUEONLY, la valeur d’heure est définie sur l’heure 0 ou minuit. Dans le cas de VAR_TIMEVALUEONLY, la valeur de date est définie sur date 0, ce qui signifie 30 décembre 1899.

Si la chaîne n’a pas pu être convertie en valeur de date/heure ou en cas de dépassement de capacité numérique, l’état de cet `COleDateTime` objet n’est pas valide.

Pour plus d’informations sur les limites et l’implémentation des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimesetdate"></a><a name="setdate"></a> COleDateTime :: SetDate

Définit la date de cet `COleDateTime` objet.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Paramètres

*nYear*\
Indique l’année à copier dans cet `COleDateTime` objet.

*nMonth*\
Indique le mois à copier dans cet `COleDateTime` objet.

*nJour*\
Indique le jour à copier dans cet `COleDateTime` objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la valeur de cet `COleDateTime` objet a été correctement définie ; sinon, 1. Cette valeur de retour est basée sur le `DateTimeStatus` type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus](#setstatus) .

### <a name="remarks"></a>Remarques

La date est définie sur les valeurs spécifiées. L’heure est définie sur l’heure 0, minuit.

Consultez le tableau suivant pour les limites des valeurs de paramètre :

|Paramètre|Bounds|
|---------------|------------|
|*nYear*|100-9999|
|*nMonth*|1 - 12|
|*nJour*|0 - 31|

Si le jour du mois déborde, il est converti au jour approprié du mois suivant et le mois et/ou l’année sont incrémentés en conséquence. Une valeur de jour égale à zéro indique le dernier jour du mois précédent. Le comportement est le même que `SystemTimeToVariantTime` .

Si la valeur de date spécifiée par les paramètres n’est pas valide, l’état de cet objet est défini sur `COleDateTime::invalid` . Vous devez utiliser [GetStatus](#getstatus) pour vérifier la validité de la `DATE` valeur et ne pas supposer que la valeur de [m_dt](#m_dt) restera inchangée.

Voici quelques exemples de valeurs de date :

|*nYear*|*nMonth*|*nJour*|Value|
|-------------|--------------|------------|-----------|
|2000|2|29|29 février 2000|
|1776|7|4|4 juillet 1776|
|1925|4|35|35 avril 1925 (date non valide)|
|10000|1|1|1 janvier 10000 (date non valide)|

Pour définir à la fois la date et l’heure, consultez [COleDateTime :: SetDateTime](#setdatetime).

Pour plus d’informations sur les fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a> COleDateTime :: SetDateTime

Définit la date et l’heure de cet `COleDateTime` objet.

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Paramètres

*nYear*, *nMonth*, *nJour*, *nheure*, *nMin*, *nSec*<br/>
Indiquer les composants de date et d’heure à copier dans cet `COleDateTime` objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la valeur de cet `COleDateTime` objet a été correctement définie ; sinon, 1. Cette valeur de retour est basée sur le `DateTimeStatus` type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus](#setstatus) .

### <a name="remarks"></a>Remarques

Consultez le tableau suivant pour les limites des valeurs de paramètre :

|Paramètre|Bounds|
|---------------|------------|
|*nYear*|100-9999|
|*nMonth*|1 - 12|
|*nJour*|0 - 31|
|*Nheure*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si le jour du mois déborde, il est converti au jour approprié du mois suivant et le mois et/ou l’année sont incrémentés en conséquence. Une valeur de jour égale à zéro indique le dernier jour du mois précédent. Le comportement est le même que [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Si la valeur de date ou d’heure spécifiée par les paramètres n’est pas valide, l’état de cet objet est défini sur non valide et la valeur de cet objet n’est pas modifiée.

Voici quelques exemples de valeurs de temps :

|*Nheure*|*nMin*|*nSec*|Valeur|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Non valide|
|9|60|0|Non valide|

Voici quelques exemples de valeurs de date :

|*nYear*|*nMonth*|*nJour*|Value|
|-------------|--------------|------------|-----------|
|1995|4|15|15 avril 1995|
|1789|7|14|17 juillet 1789|
|1925|2|30|Non valide|
|10000|1|1|Non valide|

Pour définir la date uniquement, consultez [COleDateTime :: setDate](#setdate). Pour définir l’heure uniquement, consultez [COleDateTime :: setTime](#settime).

Pour plus d’informations sur les fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetStatus](#getstatus).

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a> COleDateTime :: SetStatus

Définit l’état de cet `COleDateTime` objet.

```cpp
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Nouvelle valeur d’État pour cet `COleDateTime` objet.

### <a name="remarks"></a>Remarques

La valeur du paramètre *Status* est définie par le `DateTimeStatus` type énuméré, qui est défini dans la `COleDateTime` classe. Pour plus d’informations, consultez [COleDateTime :: GetStatus](#getstatus) .

> [!CAUTION]
> Cette fonction est destinée à des situations de programmation avancées. Cette fonction ne modifie pas les données de cet objet. Le plus souvent, il est utilisé pour définir l’État sur **null** ou **non valide**. L’opérateur d’assignation ([Operator =](#operator_eq)) et [SetDateTime](#setdatetime) définissent l’état de l’objet en fonction de la ou des valeurs sources.

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetStatus](#getstatus).

## <a name="coledatetimesettime"></a><a name="settime"></a> COleDateTime :: SetTime

Définit l’heure de cet `COleDateTime` objet.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Paramètres

*nheure*, *nMin*, *nSec*<br/>
Indique les composants de temps à copier dans cet `COleDateTime` objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la valeur de cet `COleDateTime` objet a été correctement définie ; sinon, 1. Cette valeur de retour est basée sur le `DateTimeStatus` type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus](#setstatus) .

### <a name="remarks"></a>Remarques

L’heure est définie sur les valeurs spécifiées. La date est définie sur la date 0, ce qui signifie 30 décembre 1899.

Consultez le tableau suivant pour les limites des valeurs de paramètre :

|Paramètre|Bounds|
|---------------|------------|
|*Nheure*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si la valeur d’heure spécifiée par les paramètres n’est pas valide, l’état de cet objet est défini sur non valide et la valeur de cet objet n’est pas modifiée.

Voici quelques exemples de valeurs de temps :

|*Nheure*|*nMin*|*nSec*|Valeur|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Non valide|
|9|60|0|Non valide|

Pour définir à la fois la date et l’heure, consultez [COleDateTime :: SetDateTime](#setdatetime).

Pour plus d’informations sur les fonctions membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions membres suivantes :

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure : prise en charge d’Automation](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

Consultez l’exemple pour [setDate](#setdate).

## <a name="see-also"></a>Voir aussi

[COleVariant, classe](../../mfc/reference/colevariant-class.md)<br/>
[Classe CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan, classe](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
