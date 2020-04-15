---
title: Classe COleDateTime
ms.date: 03/27/2019
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
ms.openlocfilehash: 610cbec6cb65d4e9616c5e0e0d64e729f39febcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317744"
---
# <a name="coledatetime-class"></a>Classe COleDateTime

Encapsule le `DATE` type de données utilisé dans l’automatisation OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDateTime
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Construit un objet `COleDateTime`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDateTime::Format](#format)|Génère une représentation de chaîne `COleDateTime` formatée d’un objet.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Appelez cette méthode pour obtenir `COleDateTime` le `DBTIMESTAMP` temps dans l’objet comme une structure de données.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Appelez cette méthode pour obtenir `COleDateTime` le temps dans l’objet comme une structure de données [SYSTEMTIME.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)|
|[COleDateTime::GetAsUDATE](#getasudate)|Appelez cette méthode pour obtenir `COleDateTime` le `UDATE` temps dans la structure de données.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Crée `COleDateTime` un objet qui représente l’heure actuelle (fonction de membre statique).|
|[COleDateTime::GetDay](#getday)|Retourne le `COleDateTime` jour que cet objet représente (1 - 31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Retours le jour `COleDateTime` de la semaine cet objet représente (dimanche 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Retours le jour `COleDateTime` de l’année cet objet représente (Jan 1 ' 1).|
|[COleDateTime::GetHour](#gethour)|Retourne l’heure que cet `COleDateTime` objet représente (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Retourne la `COleDateTime` minute que représente cet objet (0 - 59).|
|[COleDateTime::GetMonth](#getmonth)|Retourne le `COleDateTime` mois que cet objet représente (1 - 12).|
|[COleDateTime::GetSecond](#getsecond)|Retourne la `COleDateTime` seconde que cet objet représente (0 - 59).|
|[COleDateTime::GetStatus](#getstatus)|Obtient le statut (validité) de cet `COleDateTime` objet.|
|[COleDateTime::GetYear](#getyear)|Retourne l’année que cet `COleDateTime` objet représente.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Lit une valeur de date/heure d’une chaîne et définit la valeur de `COleDateTime`.|
|[COleDateTime::SetDate](#setdate)|Définit la valeur `COleDateTime` de cet objet à la valeur spécifiée à la date seulement.|
|[COleDateTime::SetDateTime](#setdatetime)|Définit la valeur `COleDateTime` de cet objet à la valeur spécifiée de la date/heure.|
|[COleDateTime::SetStatus](#setstatus)|Définit l’état (validité) de cet `COleDateTime` objet.|
|[COleDateTime::SetTime](#settime)|Définit la valeur `COleDateTime` de cet objet à la valeur temporelle spécifiée seulement.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime: :opérateur, COleDateTime::opérateur <, etc.](#coledatetime_relational_operators)|Comparez `COleDateTime` deux valeurs.|
|[COleDateTime::opérateur, COleDateTime::opérateur -](#operator_add_-)|Ajouter et `COleDateTime` soustraire les valeurs.|
|[COleDateTime::opérateur , COleDateTime::opérateur -MD](#operator_add_eq_-_eq)|Ajouter et soustraire `COleDateTime` `COleDateTime` une valeur de cet objet.|
|[COleDateTime::opérateur](#operator_eq)|Copie `COleDateTime` d’une valeur.|
|[COleDateTime::operator DATE, COleDateTime::operator Date](#operator_date)|Convertit `COleDateTime` une valeur `DATE` en `DATE*`a ou en .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Contient le `DATE` sous-jacent de cet `COleDateTime` objet.|
|[COleDateTime::m_status](#m_status)|Contient l’état `COleDateTime` de cet objet.|

## <a name="remarks"></a>Notes

`COleDateTime`n’a pas de classe de base.

C’est l’un des types possibles pour le type de données [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) de l’automatisation OLE. Une `COleDateTime` valeur représente une date et une valeur d’heure absolues.

Le `DATE` type est implémenté comme une valeur de point flottant. Les jours sont mesurés à partir du 30 décembre 1899, à minuit. Le tableau suivant montre quelques dates et leurs valeurs associées :

|Date|Value|
|----------|-----------|
|29 décembre 1899, minuit|-1.0|
|29 décembre 1899, 6 h|-1.25|
|30 décembre 1899, minuit|0.0|
|31 décembre 1899, minuit|1.0|
|1er janvier 1900, 6 h|2.25|

> [!CAUTION]
> Dans le tableau ci-dessus, bien que les valeurs du jour deviennent négatives avant minuit le 30 décembre 1899, les valeurs à l’heure du jour ne le sont pas. Par exemple, 6 h est toujours représenté par une valeur fractionnée de 0,25, que l’integer représentant la journée soit positif (après le 30 décembre 1899) ou négatif (avant le 30 décembre 1899). Cela signifie qu’une simple comparaison des `COleDateTime` points flottants trierait à tort un représentant 6h00 le 29/12/1899 au **plus tard** qu’un représentant 7h00 le même jour.

Les `COleDateTime` poignées de cours datent du 1er janvier au 31 décembre 9999. La `COleDateTime` classe utilise le calendrier grégorien; il ne supporte pas les dates De Julian. `COleDateTime`ignore l’heure d’été. (Voir [date et heure : Support d’automatisation](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Vous pouvez `%y` utiliser le format pour récupérer une année à deux chiffres uniquement pour les dates à partir de 1900. Si vous `%y` utilisez le format à une date antérieure à 1900, le code génère un échec ASSERT.

Ce type est également utilisé pour représenter des valeurs de date seulement ou de temps seulement. Par convention, la date du 0 (30 décembre 1899) est utilisée pour les valeurs à temps seulement et l’heure 00:00 (minuit) est utilisée pour les valeurs de date seulement.

Si vous `COleDateTime` créez un objet en utilisant une date inférieure à 100, la date est acceptée, mais les appels ultérieurs à `GetYear` `GetMonth`, `GetDay`, , `GetHour`, `GetMinute`, et `GetSecond` échouent et retournent -1. Auparavant, vous pouvez utiliser des dates à deux chiffres, mais les dates doivent être de 100 ou plus dans MFC 4.2 et plus tard.

Pour éviter les problèmes, spécifiez une date à quatre chiffres. Par exemple :

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Les opérations arithmétiques de base pour les `COleDateTime` valeurs utilisent la classe compagnon [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`valeurs définissent un intervalle de temps. La relation entre ces classes est similaire à celle entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Pour plus d’informations sur les `COleDateTime` cours et `COleDateTimeSpan` les cours, voir l’article Date et [heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Spécifications

**En-tête:** ATLComTime.h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a>Opérateurs relationnels COleDateTime

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

*Date*<br/>
Objet `COleDateTime` à comparer.

### <a name="remarks"></a>Notes

> [!NOTE]
> Un ATLASSERT se produira si l’un des deux opérands est invalide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Exemple

Les **>=** opérateurs ** \< ** **>**, **<**, , et `COleDateTime` , affirmera si l’objet est configuré à annuler.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a>COleDateTime::COleDateTime

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
Un `COleDateTime` objet existant à copier `COleDateTime` dans le nouvel objet.

*varSrc*<br/>
Une `VARIANT` structure de données `COleVariant` existante (peut-être un objet) à convertir en valeur date/temps `COleDateTime` (VT_DATE) et copiée dans le nouvel objet.

*dtSrc*<br/>
Une valeur date/heure (`DATE`) à `COleDateTime` copier dans le nouvel objet.

*timeSrc*<br/>
A `time_t` `__time64_t` ou valeur à convertir en une valeur date/heure `COleDateTime` et copié dans le nouvel objet.

*systimeSrc*<br/>
Une `SYSTEMTIME` structure à convertir en valeur date/heure et `COleDateTime` copiée dans le nouvel objet.

*dossiertimeSrc*<br/>
Une `FILETIME` structure à convertir en valeur date/heure et `COleDateTime` copiée dans le nouvel objet. A `FILETIME` utilise Universal Coordinated Time (UTC), donc si vous passez une heure locale dans la structure, vos résultats seront incorrects. Voir [Les temps de fichiers](/windows/win32/SysInfo/file-times) dans le SDK Windows pour plus d’informations.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Indiquez la date et l’heure `COleDateTime` à copier dans le nouvel objet.

*wDosDate*, *wDosTime*<br/>
Les valeurs de date et d’heure MS-DOS doivent être converties en valeur date/heure et copiées dans le nouvel `COleDateTime` objet.

*Timestamp*<br/>
Une référence à une structure [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) contenant l’heure locale actuelle.

### <a name="remarks"></a>Notes

Tous ces constructeurs `COleDateTime` créent de nouveaux objets paraspécisés à la valeur spécifiée. Le tableau suivant affiche des plages valides pour chaque composant de date et d’heure :

|Composant date/temps|Plage valide|
|--------------------------|-----------------|
|year|100 - 9999|
|month|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

Notez que la limite supérieure réelle pour la composante de jour varie en fonction des composantes du mois et de l’année. Pour plus de `SetDate` `SetDateTime` détails, consultez les fonctions ou les fonctions des membres.

Voici une brève description de chaque constructeur :

- `COleDateTime(`**)** Construit `COleDateTime` un objet para initialisé à 0 (minuit, 30 décembre 1899).

- `COleDateTime(``dateSrc` **)** Construit `COleDateTime` un objet `COleDateTime` à partir d’un objet existant.

- `COleDateTime(`*varSrc* **)** Construit `COleDateTime` un objet. Tentatives de `VARIANT` convertir une structure ou un objet [COleVariant](../../mfc/reference/colevariant-class.md) à une valeur de date/heure ( `VT_DATE`) Si cette conversion est réussie, la valeur convertie est copiée dans le nouvel `COleDateTime` objet. Si ce n’est pas `COleDateTime` le cas, la valeur de l’objet est fixée à 0 (minuit, 30 décembre 1899) et son statut d’invalide.

- `COleDateTime(``dtSrc` **)** Construit `COleDateTime` un objet `DATE` à partir d’une valeur.

- `COleDateTime(``timeSrc` **)** Construit `COleDateTime` un objet `time_t` à partir d’une valeur.

- `COleDateTime(`*systimeSrc* **)** construit `COleDateTime` un `SYSTEMTIME` objet à partir d’une valeur.

- `COleDateTime(``filetimeSrc` **)** Construit `COleDateTime` un objet `FILETIME` à partir d’une valeur. . A `FILETIME` utilise Universal Coordinated Time (UTC), donc si vous passez une heure locale dans la structure, vos résultats seront incorrects. Pour plus d’informations, voir [Les fichiers](/windows/win32/SysInfo/file-times) dans windows SDK.

- `COleDateTime(``nYear`, `nMonth` `nDay`, `nHour` `nMin`, `nSec` **)** , ) `COleDateTime` Construit un objet à partir des valeurs numériques spécifiées.

- `COleDateTime(``wDosDate`, `wDosTime` **)** Construit `COleDateTime` un objet à partir des valeurs spécifiées de date et d’heure MS-DOS.

Pour plus d’informations sur le `time_t` type de données, consultez la fonction de [temps](../../c-runtime-library/reference/time-time32-time64.md) dans la référence de la bibliothèque *Run-Time*.

Pour plus d’informations, consultez les structures [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows.

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> Le constructeur `DBTIMESTAMP` utilisant le paramètre n’est disponible que lorsque OLEDB.h est inclus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a>COleDateTime::Format

Crée une représentation formatée de la valeur date/heure.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indique l’un des drapeaux locaux suivants :

- LOCALE_NOUSEROVERRIDE Utilisez les paramètres locaux par défaut du système, au lieu des paramètres personnalisés de l’utilisateur.

- VAR_TIMEVALUEONLY Ignorer la partie de la date pendant l’analyse.

- VAR_DATEVALUEONLY Ignorer la partie de temps pendant l’analyse.

*lcid*<br/>
Indique l’ID local à utiliser pour la conversion. Pour plus d’informations sur les identifiants linguistiques, voir [Identifications linguistiques](/windows/win32/Intl/language-identifiers).

*lpszFormat (en)*<br/>
Une chaîne de formatage similaire à la `printf` chaîne de formatage. Chaque code de formatage, précédé `%`d’un signe en `COleDateTime` pourcentage, est remplacé par le composant correspondant. D’autres caractères de la chaîne de formatage sont copiés inchangés à la chaîne retournée. Pour plus d’informations, voir la fonction run-time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). La valeur et le sens `Format` des codes de formatage sont les :

- `%H`Heures dans la journée actuelle

- `%M`Procès-verbal dans l’heure actuelle

- `%S`Secondes dans la minute actuelle

- `%%`Signe de pourcentage

*nFormatID (en)*<br/>
L’ID de ressource pour la chaîne de contrôle du format.

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient la valeur formatée date/heure.

### <a name="remarks"></a>Notes

Si l’état `COleDateTime` de cet objet est nul, la valeur de retour est une chaîne vide. Si le statut est invalide, la chaîne de retour est spécifiée par la ressource de chaîne ATL_IDS_DATETIME_INVALID.

Voici une brève description des trois formulaires de cette fonction :

`Format`( *dwFlags*, *lcid*)<br/>
Ce formulaire formate la valeur en utilisant les spécifications linguistiques (ID locales) pour la date et l’heure. En utilisant les paramètres par défaut, ce formulaire imprimera la date et l’heure, à moins que la partie de temps soit de 0 (minuit), auquel cas il imprimera seulement la date, ou la partie de date est 0 (30 décembre 1899), auquel cas il imprimera juste l’heure. Si la valeur de la date/heure est de 0 (30 décembre 1899, minuit), ce formulaire avec les paramètres par défaut imprimera minuit.

`Format`( *lpszFormat*)<br/>
Ce formulaire formate la valeur en utilisant la chaîne de format qui contient des `printf`codes de formatage spéciaux qui sont précédés d’un signe de pourcentage (%), comme dans . La chaîne de formatage est passée comme un paramètre de la fonction. Pour plus d’informations sur les codes de formatage, voir [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans la référence de bibliothèque Run-Time.

`Format`( *nFormatID*)<br/>
Ce formulaire formate la valeur en utilisant la chaîne de format qui contient des `printf`codes de formatage spéciaux qui sont précédés d’un signe de pourcentage (%), comme dans . La chaîne de formatage est une ressource. L’ID de cette ressource de chaîne est passé comme paramètre. Pour plus d’informations sur les codes de formatage, voir [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans la *référence de bibliothèque Run-Time*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP

Appelez cette méthode pour obtenir `COleDateTime` le `DBTIMESTAMP` temps dans l’objet comme une structure de données.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Paramètres

*Timestamp*<br/>
Une référence à une structure [DBTimeStamp.](/dotnet/api/system.data.oledb.oledbtype)

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Stocke le temps qui en résulte dans la structure *timeStamp* référencée. La `DBTIMESTAMP` structure de données parascée par cette fonction aura son `fraction` membre réglé à zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a>COleDateTime::GetAsSystemTime

Appelez cette méthode pour obtenir `COleDateTime` le `SYSTEMTIME` temps dans l’objet comme une structure de données.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Paramètres

*sysTime (en)*<br/>
Une référence à une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir la `COleDateTime` valeur de date/heure convertie de l’objet.

### <a name="return-value"></a>Valeur de retour

Rendements VRAI en cas de succès; FALSE si la conversion échoue, ou si l’objet `COleDateTime` est NULL ou invalide.

### <a name="remarks"></a>Notes

`GetAsSystemTime`stocke le temps qui en résulte dans *l’objet sysTime* référencé. La `SYSTEMTIME` structure de données parascée par cette fonction aura son `wMilliseconds` membre réglé à zéro.

Pour plus d’informations sur `COleDateTime` les informations d’état détenues dans un objet, voir [GetStatus](#getstatus).

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a>COleDateTime::GetAsUDATE

Appelez cette méthode pour obtenir `COleDateTime` le `UDATE` temps dans l’objet comme une structure de données.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Paramètres

*uDate (en)*<br/>
Une référence `UDATE` à une structure pour recevoir la `COleDateTime` valeur de date/heure convertie de l’objet.

### <a name="return-value"></a>Valeur de retour

Rendements VRAI en cas de succès; FALSE si la conversion échoue, ou si l’objet `COleDateTime` est NULL ou invalide.

### <a name="remarks"></a>Notes

Une `UDATE` structure représente une date « déballée ».

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a>COleDateTime::GetCurrentTime

Appelez cette fonction de membre statique pour retourner la date/heure actuelle.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a>COleDateTime::GetDay

Obtient le jour du mois représenté par cette valeur de date/heure.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le jour du mois représenté par `COleDateTime` la `COleDateTime::error` valeur de cet objet ou si le jour n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 1 et 31.

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a>COleDateTime::GetDayOfWeek

Obtient le jour du mois représenté par cette valeur de date/heure.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le jour de la semaine représenté `COleDateTime` par `COleDateTime::error` la valeur de cet objet ou si le jour de la semaine n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 1 et 7, où 1 dimanche, 2 lundi, et ainsi de suite.

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfYear (en)](#getdayofyear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a>COleDateTime::GetDayOfYear

Obtient le jour de l’année représenté par cette valeur de date/heure.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le jour de l’année représenté `COleDateTime` par `COleDateTime::error` la valeur de cet objet ou si le jour de l’année n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 1 et 366, où le 1er janvier et 1.

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a>COleDateTime::GetHour

Obtient l’heure représentée par cette valeur de date/heure.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valeur de retour

L’heure représentée par la `COleDateTime` valeur `COleDateTime::error` de cet objet ou si l’heure n’a pas pu être obtenue.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 0 et 23.

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a>COleDateTime::GetMinute

Obtient la minute représentée par cette valeur de date/heure.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valeur de retour

La minute représentée par la `COleDateTime` valeur `COleDateTime::error` de cet objet ou si la minute n’a pas pu être obtenue.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 0 et 59.

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

### <a name="example"></a>Exemple

Voir l’exemple pour [GetHour](#gethour).

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a>COleDateTime::GetMonth

Obtient le mois représenté par cette valeur de date/heure.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le mois représenté par la `COleDateTime` valeur `COleDateTime::error` de cet objet ou si le mois n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 1 et 12.

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

### <a name="example"></a>Exemple

Voir l’exemple pour [GetDay](#getday).

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a>COleDateTime::GetSecond

Obtient la deuxième représentée par cette valeur de date/heure.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le second représenté par la `COleDateTime` valeur `COleDateTime::error` de cet objet ou si le second n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 0 et 59.

> [!NOTE]
> La `COleDateTime` classe ne prend pas en charge les secondes bissextiles.

Pour plus d’informations `COleDateTime`sur la mise en œuvre pour , voir l’article [Date et heure: Soutien à l’automatisation](../../atl-mfc-shared/date-and-time-automation-support.md).

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

### <a name="example"></a>Exemple

Voir l’exemple pour [GetHour](#gethour).

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a>COleDateTime::GetStatus

Obtient le statut (validité) `COleDateTime` d’un objet donné.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’état `COleDateTime` de cette valeur. Si vous `GetStatus` faites `COleDateTime` appel à un objet construit par défaut, il retournera valide. Si vous `GetStatus` appelez `COleDateTime` un objet para initialisé avec `GetStatus` le constructeur mis à nulliser, reviendra nul.

### <a name="remarks"></a>Notes

La valeur de rendement `DateTimeStatus` est définie par le type `COleDateTime` énuméré, qui est défini au sein de la classe.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Pour une brève description de ces valeurs de statut, consultez la liste suivante :

- `COleDateTime::error`Indique qu’une erreur s’est produite alors qu’elle tentait d’obtenir une partie de la valeur de la date ou de l’heure.

- `COleDateTime::valid`Indique que `COleDateTime` cet objet est valide.

- `COleDateTime::invalid`Indique que `COleDateTime` cet objet est invalide; c’est-à-dire que sa valeur peut être incorrecte.

- `COleDateTime::null`Indique que `COleDateTime` cet objet est nul, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « nul » dans le sens de base de données de « n’avoir aucune valeur », par opposition au NULL DE C.)

L’état `COleDateTime` d’un objet est invalide dans les cas suivants :

- Si sa valeur est `VARIANT` `COleVariant` définie à partir d’une valeur ou d’une valeur qui ne pourrait pas être convertie en une valeur de date/temps.

- Si sa valeur est `time_t` `SYSTEMTIME`définie `FILETIME` à partir d’un , , ou une valeur qui ne pourrait pas être convertie en une date/heure valide.

- Si sa valeur `SetDateTime` est définie par des valeurs de paramètres invalides.

- Si cet objet a subi un débordement ou un sous-flux `+=` au `-=`cours d’une opération d’affectation arithmétique, à savoir, ou .

- Si une valeur invalide a été attribuée à cet objet.

- Si l’état de cet objet `SetStatus`a été explicitement mis à invalider en utilisant .

Pour plus d’informations sur les opérations qui peuvent invalider le statut, consultez les fonctions suivantes :

- [COleDateTime (en anglais)](#coledatetime)

- [SetDateTime (en)](#setdatetime)

- [opérateur, -](#operator_add_-)

- [opérateur , --](#operator_add_eq_-_eq)

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a>COleDateTime::GetYear

Obtient l’année représentée par cette valeur de date/temps.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Valeur de retour

L’année représentée par la `COleDateTime` valeur `COleDateTime::error` de cet objet ou si l’année n’a pas pu être obtenue.

### <a name="remarks"></a>Notes

Les valeurs de rendement valides varient entre 100 et 9999, ce qui comprend le siècle.

Pour plus d’informations sur les fonctions `COleDateTime` d’autres membres qui interrogent la valeur de cet objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [GetDay](#getday).

## <a name="coledatetimem_dt"></a><a name="m_dt"></a>COleDateTime::m_dt

La `DATE` structure sous-jacente de cet `COleDateTime` objet.

```
DATE m_dt;
```

### <a name="remarks"></a>Notes

> [!CAUTION]
> Changer la valeur `DATE` de l’objet accessible par le pointeur `COleDateTime` retourné par cette fonction modifiera la valeur de cet objet. Il ne change pas `COleDateTime` l’état de cet objet.

Pour plus d’informations `DATE` sur la mise en œuvre de l’objet, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimem_status"></a><a name="m_status"></a>COleDateTime::m_status

Contient l’état `COleDateTime` de cet objet.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Notes

Le type de ce membre de `DateTimeStatus`données est le `COleDateTime` type énuméré , qui est défini dans la classe. Pour plus d’informations, voir [COleDateTime::GetStatus](#getstatus).

> [!CAUTION]
> Ce membre des données est destiné à des situations de programmation avancées. Vous devez utiliser les fonctions de membre en ligne [GetStatus](#getstatus) et [SetStatus](#setstatus). Voir `SetStatus` pour d’autres mises en garde concernant le réglage explicite de ce membre des données.

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a>COleDateTime::opérateur

Copie `COleDateTime` d’une valeur.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Notes

Ces opérateurs d’affectation surchargés copient la `COleDateTime` date de source/valeur de l’heure dans cet objet. Voici une brève description de chacun de ces opérateurs d’affectation surchargés :

- **opérateur** `dateSrc` **()** La valeur et le statut de l’opéra sont copiés dans cet `COleDateTime` objet.

- **opérateur** *(varSrc)* **)** Si la conversion de la valeur [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) (ou objet [COleVariant)](../../mfc/reference/colevariant-class.md) à une date/heure (VT_DATE) est `COleDateTime` réussie, la valeur convertie est copiée dans cet objet et son statut est défini comme valide. Si la conversion n’est pas réussie, la valeur de cet objet est fixée à zéro (30 décembre 1899, minuit) et son statut d’invalide.

- **opérateur** `dtSrc` **()** La `DATE` valeur est copiée dans cet `COleDateTime` objet et son statut est défini pour être valide.

- **opérateur** `timeSrc` **()** La `time_t` `__time64_t` valeur ou la valeur est `COleDateTime` convertie et copiée dans cet objet. Si la conversion est réussie, l’état de cet objet est défini comme valide; en cas d’échec, il est fixé à invalide.

- **opérateur** *(systimeSrc* **)** La valeur [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) est convertie `COleDateTime` et copiée dans cet objet. Si la conversion est réussie, l’état de cet objet est défini comme valide; en cas d’échec, il est fixé à invalide.

- **opérateur** `uDate` **()** La `UDATE` valeur est convertie et `COleDateTime` copiée dans cet objet. Si la conversion est réussie, l’état de cet objet est défini comme valide; en cas d’échec, il est fixé à invalide. Une `UDATE` structure représente une date « déballée ». Pour plus d’informations, voir la fonction [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **opérateur** `filetimeSrc` **()** La valeur [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) est convertie `COleDateTime` et copiée dans cet objet. Si la conversion est réussie, l’état de cet objet est défini comme valide; sinon il est mis à invalider. `FILETIME`utilise Universal Coordinated Time (UTC), donc si vous passez un temps UTC dans la structure, vos résultats seront convertis de l’heure UTC à l’heure locale, et seront stockés en temps de variante. Ce comportement est le même que dans Visual C 6.0 et Visual C.NET 2003 SP2. Pour plus d’informations, voir [Les fichiers](/windows/win32/SysInfo/file-times) dans windows SDK.

Pour plus d’informations, voir l’entrée [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) dans le SDK Windows.

Pour plus d’informations sur le `time_t` type de données, consultez la fonction de [temps](../../c-runtime-library/reference/time-time32-time64.md) dans la référence de la bibliothèque *Run-Time*.

Pour plus d’informations, consultez les structures [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows.

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a>COleDateTime::opérateur, -

Ajouter et `ColeDateTime` soustraire les valeurs.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Notes

`COleDateTime`les objets représentent des temps absolus. Les objets [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) représentent des temps relatifs. Les deux premiers opérateurs vous permettent `COleDateTimeSpan` d’ajouter `COleDateTime` et de soustraire une valeur d’une valeur. Le troisième opérateur vous permet `COleDateTime` de soustraire `COleDateTimeSpan` une valeur d’une autre pour produire une valeur.

Si l’un ou l’autre des opérandes est nul, l’état de la valeur résultante `COleDateTime` est nul.

Si la `COleDateTime` valeur résultante ne relève pas des `COleDateTime` limites des valeurs acceptables, l’état de cette valeur est invalide.

Si l’un ou l’autre des opérandes est invalide et que l’autre n’est pas nul, le statut de la valeur résultante `COleDateTime` est invalide.

L’objet **+** et **-** les `COleDateTime` opérateurs affirmeront si l’objet est configuré à nul. Voir [COleDateTime Relational Operators](#coledatetime_relational_operators) pour un exemple.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTime::opérateur ', -'

Ajouter et soustraire `ColeDateTime` `COleDateTime` une valeur de cet objet.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire une `COleDateTimeSpan` valeur à et à partir de cela `COleDateTime`. Si l’un ou l’autre des opérandes est nul, l’état de la valeur résultante `COleDateTime` est nul.

Si la `COleDateTime` valeur résultante ne relève pas des `COleDateTime` limites des valeurs acceptables, l’état de cette valeur est mis à l’invalide.

Si l’un ou l’autre des opérandes est `COleDateTime` invalide et que d’autres n’est pas nul, le statut de la valeur résultante est invalide.

Pour plus d’informations sur les valeurs valides, invalides et nulles, consultez la variable [m_status](#m_status) membre.

L’objet **+=** et **-=** les `COleDateTime` opérateurs affirmeront si l’objet est configuré à nul. Voir [COleDateTime Relational Operators](#coledatetime_relational_operators) pour un exemple.

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a>COleDateTime::opérateur DATE

Convertit `ColeDateTime` une valeur `DATE`en un .

```
operator DATE() const throw();
```

### <a name="remarks"></a>Notes

Cet opérateur `DATE` renvoie un objet dont `COleDateTime` la valeur est copiée à partir de cet objet. Pour plus d’informations `DATE` sur la mise en œuvre de l’objet, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

L’opérateur `DATE` affirmera `COleDateTime` si l’objet est configuré à nul. Voir [COleDateTime Relational Operators](#coledatetime_relational_operators) pour un exemple.

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a>COleDateTime::ParseDateTime

Parses une chaîne pour lire une valeur date/ heure.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Paramètres

*lpszDate (lpszDate)*<br/>
Un pointeur à la corde non terminée qui doit être analysé. Pour plus d'informations, consultez Notes.

*dwFlags*<br/>
Indique les indicateurs pour les paramètres locaux et l’analyse. Un ou plusieurs des drapeaux suivants :

- LOCALE_NOUSEROVERRIDE Utilisez les paramètres locaux par défaut du système, plutôt que les paramètres personnalisés de l’utilisateur.

- VAR_TIMEVALUEONLY Ignorer la partie de la date pendant l’analyse.

- VAR_DATEVALUEONLY Ignorer la partie de temps pendant l’analyse.

*lcid*<br/>
Indique l’ID local à utiliser pour la conversion.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la chaîne a été convertie avec succès en une valeur de date/temps, autrement FALSE.

### <a name="remarks"></a>Notes

Si la chaîne a été convertie avec succès en `COleDateTime` une valeur de date/temps, la valeur de cet objet est définie à cette valeur et son statut en valide.

> [!NOTE]
> Les valeurs de l’année doivent se situer entre 100 et 9999, inclusivement.

Le paramètre *lpszDate* peut prendre une variété de formats. Par exemple, les chaînes suivantes contiennent des formats de date/heure acceptables :

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

L’ID local aura également une incidence sur la question de savoir si le format de chaîne est acceptable pour la conversion en une valeur de date/temps.

Dans le cas de VAR_DATEVALUEONLY, la valeur temporelle est fixée au délai 0, ou minuit. Dans le cas de VAR_TIMEVALUEONLY, la valeur de la date est fixée à ce jour 0, c’est-à-dire le 30 décembre 1899.

Si la chaîne ne pouvait pas être convertie en une valeur de date/heure ou s’il y avait un débordement numérique, l’état de cet `COleDateTime` objet est invalide.

Pour plus d’informations sur `COleDateTime` les limites et la mise en œuvre des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimesetdate"></a><a name="setdate"></a>COleDateTime::SetDate

Définit la date `COleDateTime` de cet objet.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Paramètres

*nYear*, *nMonth*, *nDay*<br/>
Indiquez les composants de date `COleDateTime` à copier dans cet objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la `COleDateTime` valeur de cet objet a été définie avec succès; autrement, 1. Cette valeur de rendement `DateTimeStatus` est basée sur le type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus.](#setstatus)

### <a name="remarks"></a>Notes

La date est fixée aux valeurs spécifiées. L’heure est fixée à l’heure 0, minuit.

Voir le tableau suivant pour les limites pour les valeurs de paramètres:

|Paramètre|Bounds|
|---------------|------------|
|*nYear (en)*|100 - 9999|
|*nMonth (en)*|1 - 12|
|*nDay (en)*|0 - 31|

Si le jour du mois déborde, il est converti au bon jour du mois suivant et le mois et/ou l’année sont incrémentés en conséquence. Une valeur de jour de zéro indique le dernier jour du mois précédent. Le comportement est `SystemTimeToVariantTime`le même que .

Si la valeur de date spécifiée par les paramètres n’est pas valide, l’état de cet objet est fixé à `COleDateTime::invalid`. Vous devez utiliser [GetStatus](#getstatus) pour `DATE` vérifier la validité de la valeur et ne pas supposer que la valeur de [m_dt](#m_dt) restera non modifiée.

Voici quelques exemples de valeurs de date :

|*nYear (en)*|*nMonth (en)*|*nDay (en)*|Value|
|-------------|--------------|------------|-----------|
|2000|2|29|Le 29 février 2000|
|1776|7|4|Le 4 juillet 1776|
|1925|4|35|35 avril 1925 (date non valide)|
|10000|1|1|1er janvier 10000 (date non valide)|

Pour définir à la fois la date et l’heure, voir [COleDateTime::SetDateTime](#setdatetime).

Pour plus d’informations sur les fonctions des membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a>COleDateTime::SetDateTime

Définit la date et `COleDateTime` l’heure de cet objet.

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

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Indiquez les composants de la date `COleDateTime` et de l’heure à copier dans cet objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la `COleDateTime` valeur de cet objet a été définie avec succès; autrement, 1. Cette valeur de rendement `DateTimeStatus` est basée sur le type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus.](#setstatus)

### <a name="remarks"></a>Notes

Voir le tableau suivant pour les limites pour les valeurs de paramètres:

|Paramètre|Bounds|
|---------------|------------|
|*nYear (en)*|100 - 9999|
|*nMonth (en)*|1 - 12|
|*nDay (en)*|0 - 31|
|*nHour (nHour)*|0 - 23|
|*Nmin*|0 - 59|
|*nSec (en anglais)*|0 - 59|

Si le jour du mois déborde, il est converti au bon jour du mois suivant et le mois et/ou l’année sont incrémentés en conséquence. Une valeur de jour de zéro indique le dernier jour du mois précédent. Le comportement est le même que [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Si la date ou la valeur d’heure spécifiée par les paramètres n’est pas valide, l’état de cet objet est configuré invalide et la valeur de cet objet n’est pas modifiée.

Voici quelques exemples de valeurs temporelles :

|*nHour (nHour)*|*Nmin*|*nSec (en anglais)*|Valeur|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Non valide|
|9|60|0|Non valide|

Voici quelques exemples de valeurs de date :

|*nYear (en)*|*nMonth (en)*|*nDay (en)*|Value|
|-------------|--------------|------------|-----------|
|1995|4|15|Le 15 avril 1995|
|1789|7|14|Le 17 juillet 1789|
|1925|2|30|Non valide|
|10000|1|1|Non valide|

Pour définir la date seulement, voir [COleDateTime::SetDate](#setdate). Pour définir l’heure seulement, voir [COleDateTime::SetTime](#settime).

Pour plus d’informations sur les fonctions des membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [GetStatus](#getstatus).

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a>COleDateTime::SetStatus

Définit l’état `COleDateTime` de cet objet.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
La nouvelle valeur `COleDateTime` de statut pour cet objet.

### <a name="remarks"></a>Notes

La valeur du paramètre *de statut* est définie par le `DateTimeStatus` type énuméré, qui est défini au sein de la `COleDateTime` classe. Voir [COleDateTime::GetStatus](#getstatus) pour plus de détails.

> [!CAUTION]
> Cette fonction est pour les situations de programmation avancées. Cette fonction ne modifie pas les données de cet objet. Il sera le plus souvent utilisé pour définir le statut à **null ou** **invalide**. L’opérateur[d’affectation (opérateur)](#operator_eq)et [SetDateTime](#setdatetime) fixent l’état de l’objet en fonction de la valeur source.s).

### <a name="example"></a>Exemple

Voir l’exemple pour [GetStatus](#getstatus).

## <a name="coledatetimesettime"></a><a name="settime"></a>COleDateTime::SetTime

Définit l’heure `COleDateTime` de cet objet.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Paramètres

*nHour*, *nMin*, *nSec*<br/>
Indiquez les composants de temps `COleDateTime` à copier dans cet objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la `COleDateTime` valeur de cet objet a été définie avec succès; autrement, 1. Cette valeur de rendement `DateTimeStatus` est basée sur le type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus.](#setstatus)

### <a name="remarks"></a>Notes

Le temps est réglé sur les valeurs spécifiées. La date est fixée à la date 0, c’est-à-dire le 30 décembre 1899.

Voir le tableau suivant pour les limites pour les valeurs de paramètres:

|Paramètre|Bounds|
|---------------|------------|
|*nHour (nHour)*|0 - 23|
|*Nmin*|0 - 59|
|*nSec (en anglais)*|0 - 59|

Si la valeur temporelle spécifiée par les paramètres n’est pas valide, l’état de cet objet est configuré invalide et la valeur de cet objet n’est pas modifiée.

Voici quelques exemples de valeurs temporelles :

|*nHour (nHour)*|*Nmin*|*nSec (en anglais)*|Valeur|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Non valide|
|9|60|0|Non valide|

Pour définir à la fois la date et l’heure, voir [COleDateTime::SetDateTime](#setdatetime).

Pour plus d’informations sur les fonctions des membres qui interrogent la valeur de cet `COleDateTime` objet, consultez les fonctions suivantes des membres :

- [GetDay (en)](#getday)

- [GetMonth (en)](#getmonth)

- [GetYear (en)](#getyear)

- [GetHour GetHour](#gethour)

- [GetMinute GetMinute](#getminute)

- [GetSecond (en)](#getsecond)

- [GetDayOfWeek (en anglais seulement)](#getdayofweek)

- [GetDayOfYear (en)](#getdayofyear)

Pour plus d’informations `COleDateTime` sur les limites des valeurs, voir l’article [Date et heure: Automation Support](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [SetDate](#setdate).

## <a name="see-also"></a>Voir aussi

[COleVariant, classe](../../mfc/reference/colevariant-class.md)<br/>
[Classe CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[Classe CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
