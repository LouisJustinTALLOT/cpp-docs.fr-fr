---
description: 'En savoir plus sur : classe CTime'
title: Classe CTime
ms.date: 10/18/2018
f1_keywords:
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: 3768423a4d3bf873e9161b846e21fda4beffdc9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166601"
---
# <a name="ctime-class"></a>Classe CTime

Représente une date et une heure absolues.

## <a name="syntax"></a>Syntaxe

```
class CTime
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTime :: CTime](#ctime)|Construit `CTime` des objets de différentes façons.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTime :: format](#format)|Convertit un `CTime` objet en chaîne mise en forme, en fonction du fuseau horaire local.|
|[CTime :: FormatGmt](#formatgmt)|Convertit un `CTime` objet en chaîne mise en forme, en fonction du temps universel coordonné (UTC).|
|[CTime :: GetAsDBTIMESTAMP](#getasdbtimestamp)|Convertit les informations d’heure stockées dans l' `CTime` objet en une structure DBTIMESTAMP compatible Win32.|
|[CTime :: GetAsSystemTime](#getassystemtime)|Convertit les informations d’heure stockées dans l' `CTime` objet en une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible Win32.|
|[CTime :: GetCurrentTime](#getcurrenttime)|Crée un `CTime` objet qui représente l’heure actuelle (fonction membre statique).|
|[CTime :: GetDay](#getday)|Retourne le jour représenté par l' `CTime` objet.|
|[CTime :: GetDayOfWeek](#getdayofweek)|Retourne le jour de la semaine représenté par l' `CTime` objet.|
|[CTime :: GetGmtTm](#getgmttm)|Décompose un `CTime` objet en composants, en fonction du temps universel coordonné (UTC).|
|[CTime :: GetHour](#gethour)|Retourne l’heure représentée par l' `CTime` objet.|
|[CTime :: GetLocalTm](#getlocaltm)|Décompose un `CTime` objet en composants, en fonction du fuseau horaire local.|
|[CTime :: GetMinute](#getminute)|Retourne la minute représentée par l' `CTime` objet.|
|[CTime :: GetMonth](#getmonth)|Retourne le mois représenté par l' `CTime` objet.|
|[CTime :: GetSecond](#getsecond)|Retourne le deuxième représenté par l' `CTime` objet.|
|[CTime :: GetTime](#gettime)|Retourne une valeur **__time64_t** pour l' `CTime` objet donné.|
|[CTime :: GetYear](#getyear)|Retourne l’année représentée par l' `CTime` objet.|
|[CTime :: Serialize64](#serialize64)|Sérialise les données vers ou à partir d’une archive.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur +-](#operator_add_-)|Ces opérateurs ajoutent et déduisent `CTimeSpan` des `CTime` objets et.|
|[opérateur + =,-=](#operator_add_eq_-_eq)|Ces opérateurs ajoutent et déduire un `CTimeSpan` objet vers et à partir de cet `CTime` objet.|
|[opérateur =](#operator_eq)|Opérateur d’assignation.|
|[opérateur = =, <, etc.](#ctime_comparison_operators)|Opérateurs de comparaison.|

## <a name="remarks"></a>Notes

`CTime` n’a pas de classe de base.

`CTime` les valeurs sont basées sur le temps universel coordonné (UTC, Universal Time Coordinated), ce qui équivaut à l’heure universelle coordonnée (heure de Greenwich, GMT). Pour plus d’informations sur la façon dont le fuseau horaire est déterminé, consultez [gestion du temps](../../c-runtime-library/time-management.md) .

Quand vous créez un `CTime` objet, affectez au paramètre la valeur `nDST` 0 pour indiquer que l’heure standard est en vigueur, ou à une valeur supérieure à 0 pour indiquer que l’heure d’été est en vigueur ou à une valeur inférieure à zéro pour que le code de la bibliothèque Runtime C calcule si l’heure d’hiver ou l’heure d’été est en vigueur. `tm_isdst` est un champ obligatoire. S’il n’est pas défini, sa valeur est indéfinie et la valeur de retour de [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) est imprévisible. Si `timeptr` pointe vers une structure de TM retournée par un appel précédent à [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)ou [Localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), le `tm_isdst` champ contient la valeur correcte.

Une classe complémentaire, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), représente un intervalle de temps.

Les `CTime` classes et ne `CTimeSpan` sont pas conçues pour la dérivation. Étant donné qu’il n’y a aucune fonction virtuelle, la taille des `CTime` `CTimeSpan` objets et est exactement de 8 octets. La plupart des fonctions membres sont Inline.

> [!NOTE]
> La limite de date supérieure est 12/31/3000. La limite inférieure est de 1/1/1970 12:00:00 AM GMT.

Pour plus d’informations sur l’utilisation de `CTime` , consultez les articles [date et heure](../../atl-mfc-shared/date-and-time.md)et [gestion du temps](../../c-runtime-library/time-management.md) dans la référence de la bibliothèque Run-Time.

> [!NOTE]
> La `CTime` structure a changé de mfc 7,1 en mfc 8,0. Si vous sérialisez une `CTime` structure à l’aide de l' **opérateur <<** sous MFC 8,0 ou une version ultérieure, le fichier résultant ne sera pas lisible sur les versions antérieures de MFC.

## <a name="requirements"></a>Spécifications

**En-tête :** atltime. h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a> Opérateurs de comparaison CTime

Opérateurs de comparaison.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>Paramètres

*time*<br/>
Objet `CTime` à comparer.

### <a name="return-value"></a>Valeur renvoyée

Ces opérateurs comparent deux heures absolues et retournent TRUE si la condition est true ; Sinon, FALSe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a> CTime :: CTime

Crée un `CTime` objet initialisé avec l’heure spécifiée.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>Paramètres

*timeSrc*<br/>
Indique un `CTime` objet qui existe déjà.

*time*<br/>
`__time64_t`Valeur de temps, qui est le nombre de secondes après le 1er janvier 1970 UTC. Notez que cette valeur est ajustée à l’heure locale. Par exemple, si vous êtes à New York et créez un `CTime` objet en passant un paramètre de 0, [CTime :: GetMonth](#getmonth) retourne 12.

*nYear*, *nMonth*, *nJour*, *nheure*, *nMin*, *nSec*<br/>
Indique les valeurs de date et d’heure à copier dans le nouvel `CTime` objet.

*nDST*<br/>
Indique si l’heure d’été est en vigueur. Peut avoir l’une des trois valeurs suivantes :

- *nDST* a la valeur 0Standard Time est activé.

- *nDST* défini sur une valeur supérieure à 0Daylight le temps d’économie est effectif.

- *nDST* défini sur une valeur inférieure à 0The par défaut. Calcule automatiquement si l’heure d’hiver ou l’heure d’été est en vigueur.

*wDosDate*, *wDosTime*<br/>
Valeurs de date et d’heure MS-DOS à convertir en valeur de date/heure et copiées dans le nouvel `CTime` objet.

*st*<br/>
Structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) à convertir en valeur de date/heure et copiée dans le nouvel `CTime` objet.

*pied*<br/>
Structure [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) à convertir en valeur de date/heure et copiée dans le nouvel `CTime` objet.

*actuelle*<br/>
Référence à une structure DBTIMESTAMP contenant l’heure locale actuelle.

### <a name="remarks"></a>Notes

Chaque constructeur est décrit ci-dessous :

- `CTime();` Construit un objet non initialisé `CTime` . Ce constructeur vous permet de définir des `CTime` tableaux d’objets. Vous devez initialiser ces tableaux avec des heures valides avant d’utiliser.

- `CTime( const CTime& );` Construit un `CTime` objet à partir d’une autre `CTime` valeur.

- `CTime( __time64_t );` Construit un `CTime` objet à partir d’un type de **__time64_t** . Ce constructeur attend une heure UTC et convertit le résultat en heure locale avant de stocker le résultat.

- `CTime( int, int, ...);` Construit un `CTime` objet à partir de composants de l’heure locale avec chaque composant qui est soumis aux plages suivantes :

   |Composant|Plage|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nJour*|1-31|
   |*Nheure*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Ce constructeur effectue la conversion appropriée en heure UTC. La version de débogage de l’bibliothèque MFC (Microsoft Foundation Class) déclare si un ou plusieurs composants de l’heure sont hors limites. Vous devez valider les arguments avant d’appeler. Ce constructeur attend une heure locale.

- `CTime( WORD, WORD );` Construit un `CTime` objet à partir des valeurs de date et d’heure ms-dos spécifiées. Ce constructeur attend une heure locale.

- `CTime( const SYSTEMTIME& );` Construit un `CTime` objet à partir d’une `SYSTEMTIME` structure. Ce constructeur attend une heure locale.

- `CTime( const FILETIME& );` Construit un `CTime` objet à partir d’une `FILETIME` structure. Vous n’utiliserez probablement pas `CTime FILETIME` directement l’initialisation. Si vous utilisez un `CFile` objet pour manipuler un fichier, `CFile::GetStatus` récupère l’horodatage de fichier à l’aide d’un `CTime` objet initialisé à l’aide d’une `FILETIME` structure. Ce constructeur suppose une heure basée sur le temps universel coordonné (UTC) et convertit automatiquement la valeur en heure locale avant de stocker le résultat.

   > [!NOTE]
   > Le constructeur qui utilise le `DBTIMESTAMP` paramètre n’est disponible que lorsque OleDb. h est inclus.

Pour plus d’informations, consultez la structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows. Consultez également l’entrée de [date et heure ms-dos](/windows/win32/SysInfo/ms-dos-date-and-time) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a> CTime :: format

Appelez cette fonction membre pour créer une représentation mise en forme de la valeur de date et d’heure.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Chaîne de mise en forme similaire à la `printf` chaîne de mise en forme. Les codes de mise en forme, précédés d’un signe de pourcentage ( `%` ), sont remplacés par le `CTime` composant correspondant. Les autres caractères de la chaîne de mise en forme sont copiés sans modification dans la chaîne retournée. Pour obtenir la liste des codes de mise en forme, consultez la fonction runtime [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*nFormatID*<br/>
ID de la chaîne qui identifie ce format.

### <a name="return-value"></a>Valeur renvoyée

[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient l’heure mise en forme.

### <a name="remarks"></a>Notes

Si l’état de cet `CTime` objet est null, la valeur de retour est une chaîne vide.

Cette méthode lève une exception si la valeur date-heure à mettre en forme n’est pas comprise entre le 1er janvier 1970 et le 31 décembre 3000 l’heure UTC (Universal Coordinated Time).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a> CTime :: FormatGmt

Génère une chaîne mise en forme qui correspond à cet `CTime` objet.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Spécifie une chaîne de mise en forme similaire à la `printf` chaîne de mise en forme. Pour plus d’informations, consultez la fonction runtime [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*nFormatID*<br/>
ID de la chaîne qui identifie ce format.

### <a name="return-value"></a>Valeur renvoyée

[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient l’heure mise en forme.

### <a name="remarks"></a>Notes

La valeur d’heure n’est pas convertie et reflète donc le temps universel coordonné (UTC).

Cette méthode lève une exception si la valeur date-heure à mettre en forme n’est pas comprise entre le 1er janvier 1970 et le 31 décembre 3000 l’heure UTC (Universal Coordinated Time).

### <a name="example"></a>Exemple

Consultez l’exemple pour [CTime :: format](#format).

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a> CTime :: GetAsDBTIMESTAMP

Appelez cette fonction membre pour convertir les informations d’heure stockées dans l' `CTime` objet en une structure DBTIMESTAMP compatible Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Paramètres

*actuelle*<br/>
Référence à une structure DBTIMESTAMP contenant l’heure locale actuelle.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Stocke l’heure résultante dans la structure *DBTS* référencée. La `DBTIMESTAMP` structure de données initialisée par cette fonction aura son `fraction` membre défini sur zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a> CTime :: GetAsSystemTime

Appelez cette fonction membre pour convertir les informations d’heure stockées dans l' `CTime` objet en une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible Win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Paramètres

*le plus chronométré*<br/>
Référence à une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contiendra la valeur de date/heure convertie de l' `CTime` objet.

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

`GetAsSystemTime` stocke l’heure résultante dans la structure référencée la plus *minutée* . La `SYSTEMTIME` structure de données initialisée par cette fonction aura son `wMilliseconds` membre défini sur zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a> CTime :: GetCurrentTime

Retourne un `CTime` objet qui représente l’heure actuelle.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Notes

Retourne la date et l’heure système actuelles en temps universel coordonné (UTC).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a> CTime :: GetDay

Retourne le jour représenté par l' `CTime` objet.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le jour du mois, en fonction de l’heure locale, dans la plage comprise entre 1 et 31.

### <a name="remarks"></a>Notes

Cette fonction appelle `GetLocalTm` , qui utilise une mémoire tampon interne allouée statiquement. Les données de cette mémoire tampon sont remplacées en raison des appels à d’autres `CTime` fonctions membres.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a> CTime :: GetDayOfWeek

Retourne le jour de la semaine représenté par l' `CTime` objet.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le jour de la semaine en fonction de l’heure locale ; 1 = dimanche, 2 = lundi, à 7 = samedi.

### <a name="remarks"></a>Notes

Cette fonction appelle `GetLocalTm` , qui utilise une mémoire tampon interne allouée statiquement. Les données de cette mémoire tampon sont remplacées en raison des appels à d’autres `CTime` fonctions membres.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a> CTime :: GetGmtTm

Obtient un **struct TM** qui contient une décomposition de l’heure contenue dans cet `CTime` objet.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*PTM*<br/>
Pointe vers une mémoire tampon qui recevra les données d’heure. Si ce pointeur est NULL, une exception est levée.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un **struct TM** rempli tel que défini dans l’include file Time. H. Consultez [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) pour la disposition de la structure.

### <a name="remarks"></a>Notes

`GetGmtTm` retourne l’heure UTC.

*PTM* ne peut pas être null. Si vous souhaitez revenir à l’ancien comportement, dans lequel *PTM* peut avoir la valeur null pour indiquer qu’une mémoire tampon interne allouée de manière statique doit être utilisée, puis annuler la définition de _SECURE_ATL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a> CTime :: GetHour

Retourne l’heure représentée par l' `CTime` objet.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’heure, en fonction de l’heure locale, dans la plage de 0 à 23.

### <a name="remarks"></a>Notes

Cette fonction appelle `GetLocalTm` , qui utilise une mémoire tampon interne allouée statiquement. Les données de cette mémoire tampon sont remplacées en raison des appels à d’autres `CTime` fonctions membres.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a> CTime :: GetLocalTm

Obtient un **struct TM** contenant une décomposition de l’heure contenue dans cet `CTime` objet.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*PTM*<br/>
Pointe vers une mémoire tampon qui recevra les données d’heure. Si ce pointeur est NULL, une exception est levée.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un **struct TM** rempli tel que défini dans l’include file Time. H. Consultez [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) pour la disposition de la structure.

### <a name="remarks"></a>Notes

`GetLocalTm` retourne l’heure locale.

*PTM* ne peut pas être null. Si vous souhaitez revenir à l’ancien comportement, dans lequel *PTM* peut avoir la valeur null pour indiquer qu’une mémoire tampon interne allouée de manière statique doit être utilisée, puis annuler la définition de _SECURE_ATL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a> CTime :: GetMinute

Retourne la minute représentée par l' `CTime` objet.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la minute, en fonction de l’heure locale, dans la plage de 0 à 59.

### <a name="remarks"></a>Notes

Cette fonction appelle `GetLocalTm` , qui utilise une mémoire tampon interne allouée statiquement. Les données de cette mémoire tampon sont remplacées en raison des appels à d’autres `CTime` fonctions membres.

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetHour](#gethour).

## <a name="ctimegetmonth"></a><a name="getmonth"></a> CTime :: GetMonth

Retourne le mois représenté par l' `CTime` objet.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le mois, en fonction de l’heure locale, dans la plage comprise entre 1 et 12 (1 = janvier).

### <a name="remarks"></a>Notes

Cette fonction appelle `GetLocalTm` , qui utilise une mémoire tampon interne allouée statiquement. Les données de cette mémoire tampon sont remplacées en raison des appels à d’autres `CTime` fonctions membres.

### <a name="example"></a>Exemple

Consultez l’exemple pour [getDay](#getday).

## <a name="ctimegetsecond"></a><a name="getsecond"></a> CTime :: GetSecond

Retourne le deuxième représenté par l' `CTime` objet.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le second, en fonction de l’heure locale, dans la plage de 0 à 59.

### <a name="remarks"></a>Notes

Cette fonction appelle `GetLocalTm` , qui utilise une mémoire tampon interne allouée statiquement. Les données de cette mémoire tampon sont remplacées en raison des appels à d’autres `CTime` fonctions membres.

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetHour](#gethour).

## <a name="ctimegettime"></a><a name="gettime"></a> CTime :: GetTime

Retourne une valeur **__time64_t** pour l' `CTime` objet donné.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

`GetTime` retourne le nombre de secondes entre l’objet actuel `CTime` et le 1er janvier 1970.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a> CTime :: GetYear

Retourne l’année représentée par l' `CTime` objet.

```
int GetYear();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’année, en fonction de l’heure locale, dans la plage comprise entre le 1er janvier 1970 et le 18 janvier 2038 (inclusive).

### <a name="remarks"></a>Notes

Cette fonction appelle `GetLocalTm` , qui utilise une mémoire tampon interne allouée statiquement. Les données de cette mémoire tampon sont remplacées en raison des appels à d’autres `CTime` fonctions membres.

### <a name="example"></a>Exemple

Consultez l’exemple pour [getDay](#getday).

## <a name="ctimeoperator-"></a><a name="operator_eq"></a> CTime :: Operator =

Opérateur d’assignation.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Paramètres

*time*<br/>
Nouvelle valeur de date/heure.

### <a name="return-value"></a>Valeur renvoyée

Objet mis à jour `CTime` .

### <a name="remarks"></a>Notes

Cet opérateur d’assignation surchargé copie l’heure source dans cet `CTime` objet. Le stockage à l’heure interne dans un `CTime` objet est indépendant du fuseau horaire. La conversion de fuseau horaire n’est pas nécessaire pendant l’attribution.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a> CTime :: Operator +,-

Ces opérateurs ajoutent et déduisent `CTimeSpan` des `CTime` objets et.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Paramètres

*timeSpan*<br/>
`CTimeSpan`Objet à ajouter ou à soustraire.

*time*<br/>
`CTime`Objet à soustraire.

### <a name="return-value"></a>Valeur renvoyée

`CTime`Objet ou `CTimeSpan` représentant le résultat de l’opération.

### <a name="remarks"></a>Notes

`CTime` les objets représentent l’heure absolue, les `CTimeSpan` objets représentent le temps relatif. Les deux premiers opérateurs vous permettent d’ajouter et de soustraire des `CTimeSpan` objets aux `CTime` objets. Le troisième opérateur vous permet de soustraire un `CTime` objet d’un autre pour produire un `CTimeSpan` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a> CTime :: Operator + =,-=

Ces opérateurs ajoutent et déduire un `CTimeSpan` objet vers et à partir de cet `CTime` objet.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*répartis*<br/>
`CTimeSpan`Objet à ajouter ou à soustraire.

### <a name="return-value"></a>Valeur renvoyée

Objet mis à jour `CTime` .

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire un `CTimeSpan` objet à et à partir de cet `CTime` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a> CTime :: Serialize64

> [!NOTE]
> Cette méthode est uniquement disponible dans les projets MFC.

Sérialise les données associées à la variable membre vers ou à partir d’une archive.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
`CArchive`Objet que vous souhaitez mettre à jour.

### <a name="return-value"></a>Valeur renvoyée

Objet mis à jour `CArchive` .

## <a name="see-also"></a>Voir aussi

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan, classe](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
