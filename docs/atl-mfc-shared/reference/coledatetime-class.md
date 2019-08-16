---
title: COleDateTime (classe)
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
ms.openlocfilehash: a254019d1efe916365799affa3d2c5271883bafb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491258"
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
|[COleDateTime::COleDateTime](#coledatetime)|Construit un objet `COleDateTime`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDateTime::Format](#format)|Génère une représentation sous forme de chaîne `COleDateTime` mise en forme d’un objet.|
|[COleDateTime:: GetAsDBTIMESTAMP](#getasdbtimestamp)|Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la `DBTIMESTAMP` forme d’une structure de données.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la forme d’une structure de données [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .|
|[COleDateTime::GetAsUDATE](#getasudate)|Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` `UDATE` en tant que structure de données.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Crée un `COleDateTime` objet qui représente l’heure actuelle (fonction membre statique).|
|[COleDateTime::GetDay](#getday)|Retourne le jour représenté `COleDateTime` par cet objet (1-31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Retourne le jour de la semaine représenté `COleDateTime` par cet objet (dimanche = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Retourne le jour de l’année représenté `COleDateTime` par cet objet (1er janvier = 1).|
|[COleDateTime::GetHour](#gethour)|Retourne l’heure représentée `COleDateTime` par cet objet (0-23).|
|[COleDateTime::GetMinute](#getminute)|Retourne la minute que `COleDateTime` cet objet représente (0-59).|
|[COleDateTime::GetMonth](#getmonth)|Retourne le mois représenté `COleDateTime` par cet objet (1-12).|
|[COleDateTime::GetSecond](#getsecond)|Retourne le deuxième représenté `COleDateTime` par cet objet (0-59).|
|[COleDateTime::GetStatus](#getstatus)|Obtient l’État (validité) de cet `COleDateTime` objet.|
|[COleDateTime::GetYear](#getyear)|Retourne l’année représentée `COleDateTime` par cet objet.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Lit une valeur de date/heure à partir d’une chaîne et définit `COleDateTime`la valeur de.|
|[COleDateTime::SetDate](#setdate)|Affecte à la valeur de `COleDateTime` cet objet la valeur de date uniquement spécifiée.|
|[COleDateTime::SetDateTime](#setdatetime)|Affecte la valeur de date `COleDateTime` /heure spécifiée à cet objet.|
|[COleDateTime::SetStatus](#setstatus)|Définit l’État (validité) de cet `COleDateTime` objet.|
|[COleDateTime::SetTime](#settime)|Définit la valeur de cet `COleDateTime` objet à la valeur d’heure spécifiée uniquement.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime::operator ==, COleDateTime::operator <, etc.](#coledatetime_relational_operators)|Compare `COleDateTime` deux valeurs.|
|[COleDateTime:: Operator +, COleDateTime:: Operator-](#operator_add_-)|Ajouter et soustraire `COleDateTime` des valeurs.|
|[COleDateTime::operator +=, COleDateTime::operator -=](#operator_add_eq_-_eq)|Ajouter et soustraire `COleDateTime` une valeur de `COleDateTime` cet objet.|
|[COleDateTime:: Operator =](#operator_eq)|Copie une `COleDateTime` valeur.|
|[COleDateTime:: Operator DATE, COleDateTime:: Operator date *](#operator_date)|Convertit `COleDateTime` une valeur `DATE` en ou `DATE*`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Contient le sous `DATE` -jacent `COleDateTime` pour cet objet.|
|[COleDateTime::m_status](#m_status)|Contient l’état de cet `COleDateTime` objet.|

## <a name="remarks"></a>Notes

`COleDateTime`n’a pas de classe de base.

Il s’agit de l’un des types possibles pour le type de données [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) de OLE Automation. Une `COleDateTime` valeur représente une valeur de date et d’heure absolue.

Le `DATE` type est implémenté en tant que valeur à virgule flottante. Les jours sont mesurés à partir du 30 décembre 1899, à minuit. Le tableau suivant présente certaines dates et leurs valeurs associées:

|Date|`Value`|
|----------|-----------|
|29 décembre 1899, minuit|-1.0|
|29 décembre 1899, 6 A. M|-1.25|
|30 décembre 1899, minuit|0.0|
|31 décembre 1899, minuit|1.0|
|1er janvier, de 1900 à 18:00|2.25|

> [!CAUTION]
> Dans le tableau ci-dessus, bien que les valeurs de jour deviennent négatives avant minuit le 30 décembre 1899, les valeurs d’heure de la journée ne le sont pas. Par exemple, 6:00 AM est toujours représenté par une valeur fractionnaire 0,25 que l’entier représentant le jour soit positif (après le 30 décembre 1899) ou négatif (avant le 30 décembre 1899). Cela signifie qu’une simple comparaison de virgule flottante trie par erreur `COleDateTime` un représentant 6:00 AM sur 12/29/1899, en **plus** d’une comparaison représentant 7:00 AM le même jour.

La `COleDateTime` classe gère les dates comprises entre le 1er janvier 100 et le 31 décembre 9999. La `COleDateTime` classe utilise le calendrier grégorien; elle ne prend pas en charge les dates juliennes. `COleDateTime`ignore l’heure d’été. (Voir [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.)

> [!NOTE]
> Vous pouvez utiliser le `%y` format pour récupérer une année sur deux chiffres uniquement pour les dates commençant à 1900. Si vous utilisez le `%y` format à une date antérieure à 1900, le code génère un échec d’assertion.

Ce type est également utilisé pour représenter des valeurs de date ou d’heure uniquement. Par Convention, la date 0 (30 décembre 1899) est utilisée pour les valeurs de temps uniquement et l’heure 00:00 (minuit) est utilisée pour les valeurs de date uniquement.

Si vous créez un `COleDateTime` objet à l’aide d’une date antérieure à 100, la date est acceptée, mais les appels `GetMonth`suivants `GetDay`à `GetHour` `GetYear`, `GetMinute`,, `GetSecond` , et échouent et retournent-1. Auparavant, vous pouviez utiliser des dates à deux chiffres, mais les dates doivent être 100 ou supérieures dans MFC 4,2 et versions ultérieures.

Pour éviter les problèmes, spécifiez une date à quatre chiffres. Par exemple :

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Les opérations arithmétiques de `COleDateTime` base pour les valeurs utilisent la classe complémentaire [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`les valeurs définissent un intervalle de temps. La relation entre ces classes est semblable à celle entre [ctime](../../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Pour plus d’informations sur `COleDateTime` les `COleDateTimeSpan` classes et, consultez l' [article date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

## <a name="requirements"></a>Configuration requise

**En-tête :** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>Opérateurs relationnels COleDateTime

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

### <a name="remarks"></a>Notes

> [!NOTE]
>  Un ATLASSERT se produit si l’un des deux opérandes n’est pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Exemple

Les opérateurs **>=** **\<, ,et=** `COleDateTime` déclarent **sil’objetalavaleurnull.<** **>**

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>  COleDateTime::COleDateTime

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
Structure de `VARIANT` données existante (éventuellement un `COleVariant` objet) à convertir en valeur de date/heure (VT_DATE) et copiée dans le nouvel `COleDateTime` objet.

*dtSrc*<br/>
Valeur de date/heure`DATE`() à copier dans le nouvel `COleDateTime` objet.

*timeSrc*<br/>
Valeur `time_t` `COleDateTime` ou `__time64_t` à convertir en valeur de date/heure et copiées dans le nouvel objet.

*systimeSrc*<br/>
Structure à convertir en valeur de date/heure et copiée dans le nouvel `COleDateTime` objet. `SYSTEMTIME`

*filetimeSrc*<br/>
Structure à convertir en valeur de date/heure et copiée dans le nouvel `COleDateTime` objet. `FILETIME` Un `FILETIME` utilise le temps universel coordonné (UTC, Universal Coordinated Time). par conséquent, si vous transmettez une heure locale dans la structure, vos résultats sont incorrects. Pour plus d’informations, consultez [temps de fichier](/windows/win32/SysInfo/file-times) dans le SDK Windows.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Indiquez les valeurs de date et d’heure à copier dans le `COleDateTime` nouvel objet.

*wDosDate*, *wDosTime*<br/>
Valeurs de date et d’heure ms-dos à convertir en valeur de date/heure et copiées dans `COleDateTime` le nouvel objet.

*timeStamp*<br/>
Référence à une structure [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) contenant l’heure locale actuelle.

### <a name="remarks"></a>Notes

Tous ces constructeurs créent des `COleDateTime` objets initialisés à la valeur spécifiée. Le tableau suivant indique les plages valides pour chaque composant de date et d’heure:

|Composant de date/heure|Plage valide|
|--------------------------|-----------------|
|year|100 - 9999|
|month|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|dernières|0 - 59|
|tache|0 - 59|

Notez que la limite supérieure réelle pour le composant jour varie en fonction des composants mois et année. Pour plus d’informations, `SetDate` consultez `SetDateTime` les fonctions membres ou.

Vous trouverez ci-dessous une brève description de chaque constructeur:

- `COleDateTime(` **)** Construit un `COleDateTime` objet initialisé à 0 (minuit, 30 décembre 1899).

- `COleDateTime(`) Construit un `COleDateTime` objet à partir d’un `COleDateTime` objet existant. `dateSrc`

- `COleDateTime(`*varSrc* **)** Construit un `COleDateTime` objet. Tente de convertir un `VARIANT` objet structure ou [COleVariant](../../mfc/reference/colevariant-class.md) en valeur date/heure ( `VT_DATE`). Si cette conversion réussit, la valeur convertie est copiée `COleDateTime` dans le nouvel objet. Si ce n’est pas le cas, la `COleDateTime` valeur de l’objet est définie sur 0 (minuit, 30 décembre 1899) et son état sur non valide.

- `COleDateTime(`) Construit un `COleDateTime` objet à partir d' `DATE` une valeur. `dtSrc`

- `COleDateTime(`) Construit un `COleDateTime` objet à partir d' `time_t` une valeur. `timeSrc`

- `COleDateTime(`*systimeSrc* **)** Construit un `COleDateTime` objet à partir d' `SYSTEMTIME` une valeur.

- `COleDateTime(`) Construit un `COleDateTime` objet à partir d' `FILETIME` une valeur. `filetimeSrc` . Un `FILETIME` utilise le temps universel coordonné (UTC, Universal Coordinated Time). par conséquent, si vous transmettez une heure locale dans la structure, vos résultats sont incorrects. Pour plus d’informations, consultez [temps de fichier](/windows/win32/SysInfo/file-times) dans le SDK Windows.

- `COleDateTime(``nYear`, ,,`nDay`,,) Construit un objet`COleDateTime` à partir des valeurs numériques spécifiées. `nHour` `nMin` `nMonth` `nSec`

- `COleDateTime(``wDosDate`, )`wDosTime` Construit un`COleDateTime` objet à partir des valeurs de date et d’heure ms-dos spécifiées.

Pour plus d’informations sur `time_t` le type de données, consultez la fonction [Time](../../c-runtime-library/reference/time-time32-time64.md) dans la référence de la *bibliothèque*Runtime.

Pour plus d’informations, consultez les structures [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows.

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

> [!NOTE]
> Le constructeur qui `DBTIMESTAMP` utilise le paramètre n’est disponible que lorsque OleDb. h est inclus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

Crée une représentation mise en forme de la valeur de date/heure.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indique l’un des indicateurs de paramètres régionaux suivants:

- LOCALE_NOUSEROVERRIDE utilise les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.

- VAR_TIMEVALUEONLY ignore la partie date pendant l’analyse.

- VAR_DATEVALUEONLY ignore la partie heure pendant l’analyse.

*lcid*<br/>
Indique l’ID de paramètres régionaux à utiliser pour la conversion. Pour plus d’informations sur les identificateurs de langue, consultez identificateurs de [langue](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Chaîne de mise en forme similaire à `printf` la chaîne de mise en forme. Chaque code de mise en forme, précédé d’un signe `%`de pourcentage (), est remplacé par `COleDateTime` le composant correspondant. Les autres caractères de la chaîne de mise en forme sont copiés sans modification dans la chaîne retournée. Pour plus d’informations, consultez la fonction runtime [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). La valeur et la signification des codes de mise en `Format` forme pour sont les suivantes:

- `%H`Heures du jour en cours

- `%M`Minutes dans l’heure actuelle

- `%S`Secondes dans la minute actuelle

- `%%`Signe de pourcentage

*nFormatID*<br/>
ID de ressource pour la chaîne de contrôle de format.

### <a name="return-value"></a>Valeur de retour

`CString` Qui contient la valeur de date/heure mise en forme.

### <a name="remarks"></a>Notes

Si l’état de cet `COleDateTime` objet est null, la valeur de retour est une chaîne vide. Si l’État n’est pas valide, la chaîne de retour est spécifiée par la ressource de type chaîne ATL_IDS_DATETIME_INVALID.

Une brève description des trois formes pour cette fonction est la suivante:

`Format`( *dwFlags*, *lcid*)<br/>
Cette forme met en forme la valeur à l’aide des spécifications de langue (ID de paramètres régionaux) pour la date et l’heure. À l’aide des paramètres par défaut, ce formulaire affiche la date et l’heure, sauf si la partie heure a la valeur 0 (minuit), auquel cas il n’imprimera que la date, ou la partie date est 0 (30 décembre 1899), auquel cas il imprimera uniquement le temps. Si la valeur de date/heure est 0 (30 décembre 1899, minuit), cette forme avec les paramètres par défaut s’imprimera à minuit.

`Format`( *lpszFormat*)<br/>
Cette forme met en forme la valeur à l’aide de la chaîne de format qui contient des codes de mise en forme spéciaux précédés d’un `printf`signe de pourcentage (%), comme dans. La chaîne de mise en forme est transmise en tant que paramètre à la fonction. Pour plus d’informations sur les codes de mise en forme, consultez [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans la référence de la bibliothèque Runtime.

`Format`( *nFormatID*)<br/>
Cette forme met en forme la valeur à l’aide de la chaîne de format qui contient des codes de mise en forme spéciaux précédés d’un `printf`signe de pourcentage (%), comme dans. La chaîne de mise en forme est une ressource. L’ID de cette ressource de type chaîne est passé en tant que paramètre. Pour plus d’informations sur les codes de mise en forme, consultez [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans la référence de la *bibliothèque Runtime*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP

Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la `DBTIMESTAMP` forme d’une structure de données.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Paramètres

*timeStamp*<br/>
Référence à une structure [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) .

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Stocke l’heure résultante dans la structure d' *horodatage* référencée. La `DBTIMESTAMP` structure de données initialisée par cette fonction aura son `fraction` membre défini sur zéro.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la `SYSTEMTIME` forme d’une structure de données.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Paramètres

*sysTime*<br/>
Référence à une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir la valeur de date/heure convertie `COleDateTime` de l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite; False si la conversion échoue, ou si `COleDateTime` l’objet est null ou non valide.

### <a name="remarks"></a>Notes

`GetAsSystemTime`stocke l’heure résultante dans l’objet *sysTime* référencé. La `SYSTEMTIME` structure de données initialisée par cette fonction aura son `wMilliseconds` membre défini sur zéro.

Pour plus d’informations sur les informations d’État contenues dans un `COleDateTime` objet, consultez [GetStatus](#getstatus).

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

Appelez cette méthode pour obtenir l’heure de l' `COleDateTime` objet sous la `UDATE` forme d’une structure de données.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Paramètres

*uDate*<br/>
Référence à une `UDATE` structure pour recevoir la valeur de date/heure convertie `COleDateTime` de l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite; False si la conversion échoue, ou si `COleDateTime` l’objet est null ou non valide.

### <a name="remarks"></a>Notes

Une `UDATE` structure représente une date «décompressée».

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

Appelez cette fonction membre statique pour retourner la valeur de date/heure actuelle.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>  COleDateTime::GetDay

Obtient le jour du mois représenté par cette valeur de date/heure.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valeur de retour

Jour du mois représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

La plage des valeurs de retour valides est comprise entre 1 et 31.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

Obtient le jour du mois représenté par cette valeur de date/heure.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valeur de retour

Jour de la semaine représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour de la semaine n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

La plage des valeurs de retour valides est comprise entre 1 et 7, où 1 = dimanche, 2 = lundi, et ainsi de suite.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

Obtient le jour de l’année représenté par cette valeur de date/heure.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Valeur de retour

Jour de l’année représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour de l’année n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

La plage des valeurs de retour valides est comprise entre 1 et 366, où 1 janvier = 1.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>  COleDateTime::GetHour

Obtient l’heure représentée par cette valeur de date/heure.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valeur de retour

L’heure représentée par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si l’heure n’a pas pu être obtenue.

### <a name="remarks"></a>Notes

La plage des valeurs de retour valides est comprise entre 0 et 23.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

Obtient la minute représentée par cette valeur de date/heure.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valeur de retour

Minute représentée par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si la minute n’a pas pu être obtenue.

### <a name="remarks"></a>Notes

La plage des valeurs de retour valides est comprise entre 0 et 59.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetHour](#gethour).

##  <a name="getmonth"></a>  COleDateTime::GetMonth

Obtient le mois représenté par cette valeur de date/heure.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valeur de retour

Mois représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le mois n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

La plage des valeurs de retour valides est comprise entre 1 et 12.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemples

Consultez l’exemple pour [getDay](#getday).

##  <a name="getsecond"></a>  COleDateTime::GetSecond

Obtient le deuxième représenté par cette valeur de date/heure.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valeur de retour

Deuxième représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le deuxième n’a pas pu être obtenu.

### <a name="remarks"></a>Notes

La plage des valeurs de retour valides est comprise entre 0 et 59.

> [!NOTE]
>  La `COleDateTime` classe ne prend pas en charge les secondes bissextiles.

Pour plus d’informations sur l’implémentation `COleDateTime`de, consultez l' [article date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetHour](#gethour).

##  <a name="getstatus"></a>  COleDateTime::GetStatus

Obtient l’État (validité) d’un objet `COleDateTime` donné.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’état de cette `COleDateTime` valeur. Si vous appelez `GetStatus` sur un `COleDateTime` objet construit avec la valeur par défaut, il retourne la valeur valide. Si vous appelez `GetStatus` sur un `COleDateTime` objet initialisé avec le constructeur ayant la valeur null, `GetStatus` retourne la valeur null.

### <a name="remarks"></a>Notes

La valeur de retour est définie par `DateTimeStatus` le type énuméré, qui est défini dans la `COleDateTime` classe.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Pour obtenir une brève description de ces valeurs d’État, consultez la liste suivante:

- `COleDateTime::error`Indique qu’une erreur s’est produite lors de la tentative d’obtention d’une partie de la valeur de date/heure.

- `COleDateTime::valid`Indique que cet `COleDateTime` objet est valide.

- `COleDateTime::invalid`Indique que cet `COleDateTime` objet n’est pas valide; autrement dit, sa valeur peut être incorrecte.

- `COleDateTime::null`Indique que cet `COleDateTime` objet a la valeur null, c’est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de «NULL» dans le sens de la base de données «n’ayant aucune valeur C++ », par opposition à la valeur null.)

L’état d’un `COleDateTime` objet n’est pas valide dans les cas suivants:

- Si sa valeur est définie à partir `VARIANT` d' `COleVariant` une valeur ou qui n’a pas pu être convertie en valeur de date/heure.

- Si sa valeur est définie à partir `time_t`d' `SYSTEMTIME`une valeur `FILETIME` , ou qui n’a pas pu être convertie en valeur de date/heure valide.

- Si sa valeur est définie par `SetDateTime` avec des valeurs de paramètre non valides.

- Si cet objet a rencontré un dépassement de capacité positif ou négatif au cours d’une opération d' `+=` assignation `-=`arithmétique, à savoir ou.

- Si une valeur non valide a été assignée à cet objet.

- Si l’état de cet objet a été explicitement défini sur non `SetStatus`valide à l’aide de.

Pour plus d’informations sur les opérations qui peuvent affecter la valeur non valide à l’État, consultez les fonctions membres suivantes:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [opérateur +,-](#operator_add_-)

- [opérateur + =,-=](#operator_add_eq_-_eq)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>  COleDateTime::GetYear

Obtient l’année représentée par cette valeur de date/heure.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Valeur de retour

Année représentée par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si l’année n’a pas pu être obtenue.

### <a name="remarks"></a>Notes

Les valeurs de retour valides sont comprises entre 100 et 9999, ce qui comprend le siècle.

Pour plus d’informations sur les autres fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

### <a name="example"></a>Exemples

Consultez l’exemple pour [getDay](#getday).

##  <a name="m_dt"></a>  COleDateTime::m_dt

Structure sous `DATE` -jacente de `COleDateTime` cet objet.

```
DATE m_dt;
```

### <a name="remarks"></a>Notes

> [!CAUTION]
>  La modification de la valeur `DATE` dans l’objet accessible par le pointeur retourné par cette fonction modifie la valeur de `COleDateTime` cet objet. Elle ne modifie pas l’état de cet `COleDateTime` objet.

Pour plus d’informations sur l’implémentation de `DATE` l’objet, consultez l' [article date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

##  <a name="m_status"></a>  COleDateTime::m_status

Contient l’état de cet `COleDateTime` objet.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Notes

Le type de ce membre de données est le type `DateTimeStatus`énuméré, qui est défini dans la `COleDateTime` classe. Pour plus d’informations, consultez [COleDateTime:: GetStatus](#getstatus).

> [!CAUTION]
>  Ce membre de données est destiné à des situations de programmation avancées. Vous devez utiliser les fonctions membres inline [GetStatus](#getstatus) et [SetStatus](#setstatus). Pour `SetStatus` plus d’informations sur la définition explicite de ce membre de données, consultez.

##  <a name="operator_eq"></a>  COleDateTime::operator =

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

### <a name="remarks"></a>Notes

Ces opérateurs d’assignation surchargés copient la valeur de date/heure `COleDateTime` source dans cet objet. Une brève description de chaque opérateur d’assignation surchargé est la suivante:

- **Operator = (** `dateSrc` **)** la valeur et l’état de l’opérande sont copiés `COleDateTime` dans cet objet.

- **opérateur = (** *varSrc* **)** Si la conversion de la valeur [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) (ou l’objet [COleVariant](../../mfc/reference/colevariant-class.md) ) en date/heure (VT_DATE) réussit, la valeur convertie est copiée dans cet `COleDateTime` objet et son état est défini sur valide. Si la conversion échoue, la valeur de cet objet est définie à zéro (30 décembre 1899, minuit) et son état est non valide.

- **Operator = (** `dtSrc` **)** la `DATE` valeur est copiée dans `COleDateTime` cet objet et son état est défini sur valide.

- **Operator = (** `timeSrc` **)** la `time_t` valeur `__time64_t` ou est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide; en cas d’échec, la valeur est non valide.

- **opérateur = (** *systimeSrc* **)** La valeur [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide; en cas d’échec, la valeur est non valide.

- **Operator = (** `uDate` **)** la `UDATE` valeur est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide; en cas d’échec, la valeur est non valide. Une `UDATE` structure représente une date «décompressée». Pour plus d’informations, consultez la fonction [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **Operator = (** `filetimeSrc` **)** la valeur [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) est convertie et copiée dans cet `COleDateTime` objet. Si la conversion réussit, l’état de cet objet est défini sur valide; Sinon, elle a la valeur non valide. `FILETIME`utilise le temps universel coordonné (UTC, Universal Coordinated Time). par conséquent, si vous transmettez une heure UTC dans la structure, vos résultats sont convertis de l’heure UTC en heure locale et sont stockés sous forme de temps variant. Ce comportement est le même que dans Visual C++ 6,0 et visual C++.NET 2003 SP2. Pour plus d’informations, consultez [temps de fichier](/windows/win32/SysInfo/file-times) dans le SDK Windows.

Pour plus d’informations, consultez l’entrée [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) dans la SDK Windows.

Pour plus d’informations sur `time_t` le type de données, consultez la fonction [Time](../../c-runtime-library/reference/time-time32-time64.md) dans la référence de la *bibliothèque*Runtime.

Pour plus d’informations, consultez les structures [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows.

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

##  <a name="operator_add_-"></a>  COleDateTime::operator +, -

Ajouter et soustraire `ColeDateTime` des valeurs.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Notes

`COleDateTime`les objets représentent des heures absolues. Les objets [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) représentent les heures relatives. Les deux premiers opérateurs vous permettent d’ajouter et de soustraire une `COleDateTimeSpan` valeur d’une `COleDateTime` valeur. Le troisième opérateur vous permet de soustraire `COleDateTime` une valeur d’une autre pour `COleDateTimeSpan` produire une valeur.

Si l’un des opérandes est null, l’état de la valeur `COleDateTime` résultante est null.

Si la valeur `COleDateTime` résultante se trouve en dehors des limites des valeurs acceptables, l' `COleDateTime` état de cette valeur n’est pas valide.

Si l’un des opérandes n’est pas valide et que l’autre n’est pas null, l' `COleDateTime` état de la valeur résultante n’est pas valide.

Les **+** opérateurs **-** et déclarent si l' `COleDateTime` objet a la valeur null. Pour obtenir un exemple, consultez la rubrique relative aux [opérateurs relationnels COleDateTime](#coledatetime_relational_operators) .

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTime::operator +=, -=

Ajouter et soustraire `ColeDateTime` une valeur de `COleDateTime` cet objet.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire une `COleDateTimeSpan` valeur à ce. `COleDateTime` Si l’un des opérandes est null, l’état de la valeur `COleDateTime` résultante est null.

Si la valeur `COleDateTime` résultante se trouve en dehors des limites des valeurs acceptables, l' `COleDateTime` état de cette valeur est défini sur non valide.

Si l’un des opérandes n’est pas valide et que l’autre n’est pas null, `COleDateTime` l’état de la valeur résultante n’est pas valide.

Pour plus d’informations sur les valeurs d’état valides, non valides et null, consultez la variable de membre [m_status](#m_status) .

Les **+=** opérateurs **-=** et déclarent si l' `COleDateTime` objet a la valeur null. Pour obtenir un exemple, consultez la rubrique relative aux [opérateurs relationnels COleDateTime](#coledatetime_relational_operators) .

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

##  <a name="operator_date"></a>COleDateTime:: Operator DATE

Convertit `ColeDateTime` une valeur `DATE`en.

```
operator DATE() const throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne un `DATE` objet dont la valeur est copiée `COleDateTime` à partir de cet objet. Pour plus d’informations sur l’implémentation de `DATE` l’objet, consultez l' [article date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

L' `DATE` opérateur déclare si l’objet `COleDateTime` a la valeur null. Pour obtenir un exemple, consultez la rubrique relative aux [opérateurs relationnels COleDateTime](#coledatetime_relational_operators) .

##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime

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
Indique des indicateurs pour les paramètres régionaux et l’analyse. Un ou plusieurs des indicateurs suivants:

- LOCALE_NOUSEROVERRIDE utilise les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.

- VAR_TIMEVALUEONLY ignore la partie date pendant l’analyse.

- VAR_DATEVALUEONLY ignore la partie heure pendant l’analyse.

*lcid*<br/>
Indique l’ID de paramètres régionaux à utiliser pour la conversion.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la chaîne a été correctement convertie en valeur de date/heure; sinon, FALSe.

### <a name="remarks"></a>Notes

Si la chaîne a été correctement convertie en valeur de date/heure, la `COleDateTime` valeur de cet objet est définie sur cette valeur et son état sur valide.

> [!NOTE]
>  Les valeurs d’année doivent être comprises entre 100 et 9999, inclus.

Le paramètre *lpszDate* peut prendre plusieurs formats. Par exemple, les chaînes suivantes contiennent des formats de date/heure acceptables:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

L’ID de paramètres régionaux détermine également si le format de chaîne est acceptable pour la conversion en une valeur de date/heure.

Dans le cas de VAR_DATEVALUEONLY, la valeur d’heure est définie sur l’heure 0 ou minuit. Dans le cas de VAR_TIMEVALUEONLY, la valeur de date est définie sur la date 0, ce qui signifie 30 décembre 1899.

Si la chaîne n’a pas pu être convertie en valeur de date/heure ou en cas de dépassement de capacité numérique `COleDateTime` , l’état de cet objet n’est pas valide.

Pour plus d’informations sur les limites et l’implémentation `COleDateTime` des valeurs, consultez l' [article date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

##  <a name="setdate"></a>  COleDateTime::SetDate

Définit la date de cet `COleDateTime` objet.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Paramètres

*nYear*, *nMonth*, *nDay*<br/>
Indiquer les composants de date à copier dans cet `COleDateTime` objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la valeur de cet `COleDateTime` objet a été correctement définie; sinon, 1. Cette valeur de retour est basée sur `DateTimeStatus` le type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus](#setstatus) .

### <a name="remarks"></a>Notes

La date est définie sur les valeurs spécifiées. L’heure est définie sur l’heure 0, minuit.

Consultez le tableau suivant pour les limites des valeurs de paramètre:

|Paramètre|Limites|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

Si le jour du mois déborde, il est converti au jour approprié du mois suivant et le mois et/ou l’année sont incrémentés en conséquence. Une valeur de jour égale à zéro indique le dernier jour du mois précédent. Le comportement est le même que `SystemTimeToVariantTime`.

Si la valeur de date spécifiée par les paramètres n’est pas valide, l’état de cet objet est `COleDateTime::invalid`défini sur. Vous devez utiliser [GetStatus](#getstatus) pour vérifier la validité de la `DATE` valeur et ne pas supposer que la valeur de [m_dt](#m_dt) reste inchangée.

Voici quelques exemples de valeurs de date:

|*nYear*|*nMonth*|*nDay*|Valeur|
|-------------|--------------|------------|-----------|
|2000|2|29|29 février 2000|
|1776|7|4|4 juillet 1776|
|1925|4|35|35 avril 1925 (date non valide)|
|10000|1|1|1 janvier 10000 (date non valide)|

Pour définir à la fois la date et l’heure, consultez [COleDateTime:: SetDateTime](#setdatetime).

Pour plus d’informations sur les fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

Définit la date et l’heure de `COleDateTime` cet objet.

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
Indiquer les composants de date et d’heure à copier dans `COleDateTime` cet objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la valeur de cet `COleDateTime` objet a été correctement définie; sinon, 1. Cette valeur de retour est basée sur `DateTimeStatus` le type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus](#setstatus) .

### <a name="remarks"></a>Notes

Consultez le tableau suivant pour les limites des valeurs de paramètre:

|Paramètre|Limites|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*Nheure*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si le jour du mois déborde, il est converti au jour approprié du mois suivant et le mois et/ou l’année sont incrémentés en conséquence. Une valeur de jour égale à zéro indique le dernier jour du mois précédent. Le comportement est le même que [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Si la valeur de date ou d’heure spécifiée par les paramètres n’est pas valide, l’état de cet objet est défini sur non valide et la valeur de cet objet n’est pas modifiée.

Voici quelques exemples de valeurs de temps:

|*Nheure*|*nMin*|*nSec*|Valeur|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Non valide|
|9|60|0|Non valide|

Voici quelques exemples de valeurs de date:

|*nYear*|*nMonth*|*nDay*|`Value`|
|-------------|--------------|------------|-----------|
|1995|4|15|15 avril 1995|
|1789|7|14|17 juillet 1789|
|1925|2|30|Non valide|
|10000|1|1|Non valide|

Pour définir la date uniquement, consultez [COleDateTime:: setDate](#setdate). Pour définir l’heure uniquement, consultez [COleDateTime:: setTime](#settime).

Pour plus d’informations sur les fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

### <a name="example"></a>Exemples

Consultez l’exemple pour [GetStatus](#getstatus).

##  <a name="setstatus"></a>  COleDateTime::SetStatus

Définit l’état de cet `COleDateTime` objet.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Paramètres

*status*<br/>
Nouvelle valeur d’État pour cet `COleDateTime` objet.

### <a name="remarks"></a>Notes

La valeur du paramètre Status est définie `DateTimeStatus` par le type énuméré, qui est défini dans `COleDateTime` la classe. Pour plus d’informations, consultez [COleDateTime:: GetStatus](#getstatus) .

> [!CAUTION]
>  Cette fonction est destinée à des situations de programmation avancées. Cette fonction ne modifie pas les données de cet objet. Le plus souvent, il est utilisé pour définir l’État sur **null** ou **non valide**. L’opérateur d’assignation ([Operator =](#operator_eq)) et [SetDateTime](#setdatetime) définissent l’état de l’objet en fonction de la ou des valeurs sources.

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetStatus](#getstatus).

##  <a name="settime"></a>  COleDateTime::SetTime

Définit l’heure de cet `COleDateTime` objet.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Paramètres

*nHour*, *nMin*, *nSec*<br/>
Indique les composants de temps à copier dans cet `COleDateTime` objet.

### <a name="return-value"></a>Valeur de retour

Zéro si la valeur de cet `COleDateTime` objet a été correctement définie; sinon, 1. Cette valeur de retour est basée sur `DateTimeStatus` le type énuméré. Pour plus d’informations, consultez la fonction membre [SetStatus](#setstatus) .

### <a name="remarks"></a>Notes

L’heure est définie sur les valeurs spécifiées. La date est définie sur la date 0, ce qui signifie 30 décembre 1899.

Consultez le tableau suivant pour les limites des valeurs de paramètre:

|Paramètre|Limites|
|---------------|------------|
|*Nheure*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si la valeur d’heure spécifiée par les paramètres n’est pas valide, l’état de cet objet est défini sur non valide et la valeur de cet objet n’est pas modifiée.

Voici quelques exemples de valeurs de temps:

|*Nheure*|*nMin*|*nSec*|Valeur|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Non valide|
|9|60|0|Non valide|

Pour définir à la fois la date et l’heure, consultez [COleDateTime:: SetDateTime](#setdatetime).

Pour plus d’informations sur les fonctions membres qui interrogent `COleDateTime` la valeur de cet objet, consultez les fonctions membres suivantes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Pour plus d’informations sur les limites des `COleDateTime` valeurs, consultez l’article [date et heure: Prise en](../../atl-mfc-shared/date-and-time-automation-support.md)charge d’Automation.

### <a name="example"></a>Exemple

Consultez l’exemple pour [setDate](#setdate).

## <a name="see-also"></a>Voir aussi

[COleVariant, classe](../../mfc/reference/colevariant-class.md)<br/>
[CTime, classe](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan, classe](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
