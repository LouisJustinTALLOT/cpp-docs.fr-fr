---
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
ms.openlocfilehash: e6e471fe648c5fa370cce750e8569e158eb1ffe4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317566"
---
# <a name="ctime-class"></a>Classe CTime

Représente un heure et une date absolues.

## <a name="syntax"></a>Syntaxe

```
class CTime
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTime::CTime](#ctime)|Construit `CTime` des objets de différentes manières.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTime::Format](#format)|Convertit `CTime` un objet en une chaîne formatée, basée sur le fuseau horaire local.|
|[CTime::FormatGmt](#formatgmt)|Convertit `CTime` un objet en une chaîne formatée, basée sur UTC.|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Convertit les informations de `CTime` temps stockées dans l’objet en une structure DBTIMESTAMP compatible avec Win32.|
|[CTime::GetAsSystemTime](#getassystemtime)|Convertit les informations temporelles stockées dans l’objet `CTime` en une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible avec Win32.|
|[CTime::GetCurrentTime](#getcurrenttime)|Crée `CTime` un objet qui représente l’heure actuelle (fonction de membre statique).|
|[CTime::GetDay](#getday)|Retourne le jour `CTime` représenté par l’objet.|
|[CTime::GetDayOfWeek](#getdayofweek)|Retourne le jour de la `CTime` semaine représenté par l’objet.|
|[CTime::GetGmtTm](#getgmttm)|Décompose un `CTime` objet en composants — basé sur UTC.|
|[CTime::GetHour](#gethour)|Retourne l’heure représentée `CTime` par l’objet.|
|[CTime::GetLocalTm](#getlocaltm)|Décompose un `CTime` objet en composants — en fonction du fuseau horaire local.|
|[CTime::GetMinute](#getminute)|Retourne la minute représentée `CTime` par l’objet.|
|[CTime::GetMonth](#getmonth)|Retourne le mois représenté `CTime` par l’objet.|
|[CTime::GetSecond](#getsecond)|Retourne le second représenté `CTime` par l’objet.|
|[CTime::GetTime](#gettime)|Retourne une **valeur __time64_t** pour `CTime` l’objet donné.|
|[CTime::GetYear](#getyear)|Retourne l’année représentée `CTime` par l’objet.|
|[CTime::Serialize64](#serialize64)|Sérialise les données à partir ou à partir d’une archive.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur -](#operator_add_-)|Ces opérateurs ajoutent `CTimeSpan` et `CTime` soustraisent et soustraisent des objets.|
|[opérateur , --](#operator_add_eq_-_eq)|Ces opérateurs ajoutent et `CTimeSpan` soustraisent `CTime` un objet à cet objet et à partir de celui-ci.|
|[opérateur](#operator_eq)|L’opérateur de l’affectation.|
|[l’opérateur, <, etc.](#ctime_comparison_operators)|Opérateurs de comparaison.|

## <a name="remarks"></a>Notes

`CTime`n’a pas de classe de base.

`CTime`sont basées sur le temps universel coordonné (UTC), qui est équivalent à l’heure universelle coordonnée (Temps moyen de Greenwich, GMT). Consultez [la gestion du temps](../../c-runtime-library/time-management.md) pour obtenir de l’information sur la façon dont le fuseau horaire est déterminé.

Lorsque vous `CTime` créez un `nDST` objet, définissez le paramètre à 0 pour indiquer que l’heure standard est en vigueur, ou à une valeur supérieure à 0 pour indiquer que l’heure d’été est en vigueur, ou à une valeur inférieure à zéro pour que le code de bibliothèque C soit calculé, que l’heure normale ou l’heure d’été soit en vigueur. `tm_isdst` est un champ obligatoire. Si elle n’est pas définie, sa valeur n’est pas définie et la valeur de retour de [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) est imprévisible. Si `timeptr` les points à une structure tm retourné par un appel précédent à [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md) `tm_isdst` , [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), ou [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), le champ contient la valeur correcte.

Une classe compagnon, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), représente un intervalle de temps.

Les `CTime` `CTimeSpan` cours et les classes ne sont pas conçus pour la dérivation. Parce qu’il n’y a `CTime` `CTimeSpan` pas de fonctions virtuelles, la taille et les objets est exactement 8 octets. La plupart des fonctions des membres sont inline.

> [!NOTE]
> La limite de date supérieure est de 12/31/3000. La limite inférieure est 1/1/1970 12:00:00 AM GMT.

Pour plus d’informations sur l’utilisation `CTime`, voir les articles Date and [Time](../../atl-mfc-shared/date-and-time.md), et Time [Management](../../c-runtime-library/time-management.md) dans la référence de la bibliothèque Run-Time.

> [!NOTE]
> La `CTime` structure est passée de MFC 7.1 à MFC 8.0. Si vous sérialisez une `CTime` structure en utilisant **l’opérateur <<** sous MFC 8.0 ou une version ultérieure, le fichier résultant ne sera pas lisible sur les anciennes versions de MFC.

## <a name="requirements"></a>Spécifications

**En-tête:** atltime.h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a>Opérateurs de comparaison CTime

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

*Temps*<br/>
Objet `CTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Ces opérateurs comparent deux fois absolues et retournent VRAI si la condition est vraie; autrement FALSE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a>CTime::CTime

Crée un `CTime` nouvel objet para initialisé avec le temps spécifié.

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
Indique `CTime` un objet qui existe déjà.

*Temps*<br/>
Une `__time64_t` valeur temporelle, qui est le nombre de secondes après Janvier 1, 1970 UTC. Notez que cela sera ajusté à votre heure locale. Par exemple, si vous êtes à `CTime` New York et créez un objet en passant un paramètre de 0, [CTime::GetMonth](#getmonth) retournera 12.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Indique la date et l’heure à `CTime` copier dans le nouvel objet.

*nDST (en)*<br/>
Indique si l’heure d’été est en vigueur. Peut avoir l’une des trois valeurs:

- *nDST* réglé à 0Standard temps est en vigueur.

- *nDST* réglé à une valeur supérieure à 0Daylight temps d’épargne est en vigueur.

- *nDST* réglé à une valeur inférieure à 0Le défaut. Calcul automatiquement si l’heure normale ou l’heure d’été est en vigueur.

*wDosDate*, *wDosTime*<br/>
Les valeurs de date et d’heure MS-DOS doivent être converties en valeur date/heure et copiées dans le nouvel `CTime` objet.

*st*<br/>
Une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) à convertir en valeur date/heure et `CTime` copiée dans le nouvel objet.

*Ft*<br/>
Une structure [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) à convertir en valeur date/heure et `CTime` copiée dans le nouvel objet.

*dbts*<br/>
Une référence à une structure DBTIMESTAMP contenant l’heure locale actuelle.

### <a name="remarks"></a>Notes

Chaque constructeur est décrit ci-dessous :

- `CTime();`Construit un objet uninitialisé. `CTime` Ce constructeur vous permet `CTime` de définir les tableaux d’objets. Vous devez initialiser ces tableaux avec des temps valides avant d’utiliser.

- `CTime( const CTime& );`Construit un `CTime` objet `CTime` à partir d’une autre valeur.

- `CTime( __time64_t );`Construit un `CTime` objet à partir **d’un type __time64_t.** Ce constructeur s’attend à un temps UTC et convertit le résultat en une heure locale avant de stocker le résultat.

- `CTime( int, int, ...);`Construit un `CTime` objet à partir de composants de l’heure locale avec chaque composant limité aux plages suivantes :

   |Composant|Plage|
   |---------------|-----------|
   |*nYear (en)*|1970-3000|
   |*nMonth (en)*|1-12|
   |*nDay (en)*|1-31|
   |*nHour (nHour)*|0-23|
   |*Nmin*|0-59|
   |*nSec (en anglais)*|0-59|

   Ce constructeur effectue la conversion appropriée à UTC. La version Debug de la Microsoft Foundation Class Library affirme si un ou plusieurs des composants de temps sont hors de portée. Vous devez valider les arguments avant d’appeler. Ce constructeur s’attend à une heure locale.

- `CTime( WORD, WORD );`Construit un `CTime` objet à partir des valeurs spécifiées de date et d’heure MS-DOS. Ce constructeur s’attend à une heure locale.

- `CTime( const SYSTEMTIME& );`Construit un `CTime` objet `SYSTEMTIME` à partir d’une structure. Ce constructeur s’attend à une heure locale.

- `CTime( const FILETIME& );`Construit un `CTime` objet `FILETIME` à partir d’une structure. Vous n’utiliserez `CTime FILETIME` probablement pas l’initialisation directement. Si vous `CFile` utilisez un objet `CFile::GetStatus` pour manipuler un fichier, récupère `CTime` le cachet `FILETIME` de temps de fichier pour vous à travers un objet initialisé avec une structure. Ce constructeur assume un temps basé sur UTC et convertit automatiquement la valeur à l’heure locale avant de stocker le résultat.

   > [!NOTE]
   > Le constructeur `DBTIMESTAMP` utilisant le paramètre n’est disponible que lorsque OLEDB.h est inclus.

Pour plus d’informations, consultez la structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) et [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) dans le SDK Windows. Voir également l’entrée [MS-DOS Date et Heure](/windows/win32/SysInfo/ms-dos-date-and-time) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a>CTime::Format

Appelez cette fonction de membre pour créer une représentation formatée de la valeur de date-temps.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Une chaîne de formatage similaire à la `printf` chaîne de formatage. Les codes de formatage,`%`précédés d’un signe `CTime` en pourcentage, sont remplacés par le composant correspondant. D’autres caractères de la chaîne de formatage sont copiés inchangés à la chaîne retournée. Consultez la fonction run-time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour une liste de codes de formatage.

*nFormatID (en)*<br/>
L’ID de la chaîne qui identifie ce format.

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient le temps formaté.

### <a name="remarks"></a>Notes

Si l’état `CTime` de cet objet est nul, la valeur de retour est une chaîne vide.

Cette méthode fait exception si la valeur de l’heure de la date au format ne varie pas de minuit, du 1er janvier 1970 au 31 décembre 3000, heure universelle coordonnée (UTC).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a>CTime::FormatGmt

Génère une chaîne formatée qui `CTime` correspond à cet objet.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Paramètres

*pszFormat*<br/>
Spécifie une chaîne `printf` de formatage similaire à la chaîne de formatage. Voir la fonction de temps d’exécution [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour plus de détails.

*nFormatID (en)*<br/>
L’ID de la chaîne qui identifie ce format.

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient le temps formaté.

### <a name="remarks"></a>Notes

La valeur temporelle n’est pas convertie et reflète donc UTC.

Cette méthode fait exception si la valeur de l’heure de la date au format ne varie pas de minuit, du 1er janvier 1970 au 31 décembre 3000, heure universelle coordonnée (UTC).

### <a name="example"></a>Exemple

Voir l’exemple pour [CTime::Format](#format).

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>CTime::GetAsDBTIMESTAMP

Appelez cette fonction membre pour convertir `CTime` les informations de temps stockées dans l’objet en une structure DBTIMESTAMP compatible Avec Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Paramètres

*dbts*<br/>
Une référence à une structure DBTIMESTAMP contenant l’heure locale actuelle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Stocke le temps qui en résulte dans la structure *de dbts* référencée. La `DBTIMESTAMP` structure de données parascée par cette fonction aura son `fraction` membre réglé à zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a>CTime::GetAsSystemTime

Appelez cette fonction membre pour convertir `CTime` les informations de temps stockées dans l’objet en une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) compatible Avec Win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Paramètres

*timeDest*<br/>
Une référence à une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui conservera la `CTime` valeur de date/heure convertie de l’objet.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

`GetAsSystemTime`stocke le temps qui en résulte dans la structure *timeDest* référencée. La `SYSTEMTIME` structure de données parascée par cette fonction aura son `wMilliseconds` membre réglé à zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a>CTime::GetCurrentTime

Retourne `CTime` un objet qui représente l’heure actuelle.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Notes

Renvoie la date et l’heure actuelles du système dans l’heure universelle coordonnée (UTC).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a>CTime::GetDay

Retourne le jour `CTime` représenté par l’objet.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le jour du mois, en fonction de l’heure locale, dans la gamme 1 à 31.

### <a name="remarks"></a>Notes

Cette fonction `GetLocalTm`appelle , qui utilise un tampon interne, statiquement alloué. Les données de ce tampon sont écrasées en raison d’appels à d’autres `CTime` fonctions de membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a>CTime::GetDayOfWeek

Retourne le jour de la `CTime` semaine représenté par l’objet.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le jour de la semaine en fonction de l’heure locale; 1 - Dimanche, 2 - Lundi, à 7 - Samedi.

### <a name="remarks"></a>Notes

Cette fonction `GetLocalTm`appelle , qui utilise un tampon interne statiquement alloué. Les données de ce tampon sont écrasées en raison d’appels à d’autres `CTime` fonctions de membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a>CTime::GetGmtTm

Obtient un **tm struct qui** contient une décomposition `CTime` du temps contenue dans cet objet.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*Ptm*<br/>
Indique un tampon qui recevra les données de temps. Si ce pointeur est NULL, une exception est lancée.

### <a name="return-value"></a>Valeur de retour

Un pointeur à un **tm struct** rempli tel que défini dans le fichier TIME inclure. H. Voir [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) pour la disposition de la structure.

### <a name="remarks"></a>Notes

`GetGmtTm`retourne UTC.

*ptm* ne peut pas être NULL. Si vous voulez revenir à l’ancien comportement, dans lequel *ptm* pourrait être NULL pour indiquer qu’un interne, tampon statiquement alloué doit être utilisé, puis indéfini _SECURE_ATL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a>CTime::GetHour

Retourne l’heure représentée `CTime` par l’objet.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’heure, en fonction de l’heure locale, dans la gamme 0 à 23.

### <a name="remarks"></a>Notes

Cette fonction `GetLocalTm`appelle , qui utilise un tampon interne statiquement alloué. Les données de ce tampon sont écrasées en raison d’appels à d’autres `CTime` fonctions de membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a>CTime::GetLocalTm

Obtient un **tm struct** contenant une décomposition du `CTime` temps contenue dans cet objet.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*Ptm*<br/>
Indique un tampon qui recevra les données de temps. Si ce pointeur est NULL, une exception est lancée.

### <a name="return-value"></a>Valeur de retour

Un pointeur à un **tm struct** rempli tel que défini dans le fichier TIME inclure. H. Voir [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) pour la disposition de la structure.

### <a name="remarks"></a>Notes

`GetLocalTm`retourne l’heure locale.

*ptm* ne peut pas être NULL. Si vous voulez revenir à l’ancien comportement, dans lequel *ptm* pourrait être NULL pour indiquer qu’un interne, tampon statiquement alloué doit être utilisé, puis indéfini _SECURE_ATL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a>CTime::GetMinute

Retourne la minute représentée `CTime` par l’objet.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la minute, en fonction de l’heure locale, dans la gamme 0 à 59.

### <a name="remarks"></a>Notes

Cette fonction `GetLocalTm`appelle , qui utilise un tampon interne statiquement alloué. Les données de ce tampon sont écrasées en raison d’appels à d’autres `CTime` fonctions de membre.

### <a name="example"></a>Exemple

Voir l’exemple pour [GetHour](#gethour).

## <a name="ctimegetmonth"></a><a name="getmonth"></a>CTime::GetMonth

Retourne le mois représenté `CTime` par l’objet.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le mois, en fonction de l’heure locale, dans la gamme 1 à 12 (1 - Janvier).

### <a name="remarks"></a>Notes

Cette fonction `GetLocalTm`appelle , qui utilise un tampon interne statiquement alloué. Les données de ce tampon sont écrasées en raison d’appels à d’autres `CTime` fonctions de membre.

### <a name="example"></a>Exemple

Voir l’exemple pour [GetDay](#getday).

## <a name="ctimegetsecond"></a><a name="getsecond"></a>CTime::GetSecond

Retourne le second représenté `CTime` par l’objet.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le second, en fonction de l’heure locale, dans la gamme 0 à 59.

### <a name="remarks"></a>Notes

Cette fonction `GetLocalTm`appelle , qui utilise un tampon interne statiquement alloué. Les données de ce tampon sont écrasées en raison d’appels à d’autres `CTime` fonctions de membre.

### <a name="example"></a>Exemple

Voir l’exemple pour [GetHour](#gethour).

## <a name="ctimegettime"></a><a name="gettime"></a>CTime::GetTime

Retourne une **valeur __time64_t** pour `CTime` l’objet donné.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Valeur de retour

`GetTime`retournera le nombre de `CTime` secondes entre l’objet actuel et le 1er janvier 1970.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a>CTime::GetYear

Retourne l’année représentée `CTime` par l’objet.

```
int GetYear();
```

### <a name="return-value"></a>Valeur de retour

Retours de l’année, en fonction de l’heure locale, dans la gamme Janvier 1,1970, au 18 Janvier 2038 (inclus).

### <a name="remarks"></a>Notes

Cette fonction `GetLocalTm`appelle , qui utilise un tampon interne statiquement alloué. Les données de ce tampon sont écrasées en raison d’appels à d’autres `CTime` fonctions de membre.

### <a name="example"></a>Exemple

Voir l’exemple pour [GetDay](#getday).

## <a name="ctimeoperator-"></a><a name="operator_eq"></a>CTime::opérateur

L’opérateur de l’affectation.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Paramètres

*Temps*<br/>
La nouvelle date/valeur de l’heure.

### <a name="return-value"></a>Valeur de retour

L’objet mis à jour. `CTime`

### <a name="remarks"></a>Notes

Cet opérateur d’affectation surchargé copie `CTime` le temps source dans cet objet. Le stockage de `CTime` temps interne dans un objet est indépendant du fuseau horaire. La conversion du fuseau horaire n’est pas nécessaire pendant l’affectation.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a>CTime::opérateur, -

Ces opérateurs ajoutent `CTimeSpan` et `CTime` soustraisent et soustraisent des objets.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Paramètres

*Timespan*<br/>
L’objet `CTimeSpan` à ajouter ou à soustraire.

*Temps*<br/>
L’objet `CTime` à soustraire.

### <a name="return-value"></a>Valeur de retour

A `CTime` `CTimeSpan` ou objet représentant le résultat de l’opération.

### <a name="remarks"></a>Notes

`CTime`objets représentent le `CTimeSpan` temps absolu, les objets représentent le temps relatif. Les deux premiers opérateurs vous permettent `CTimeSpan` d’ajouter `CTime` et de soustraire des objets vers et depuis les objets. Le troisième opérateur vous permet `CTime` de soustraire `CTimeSpan` un objet d’un autre pour donner un objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a>CTime::opérateur ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '

Ces opérateurs ajoutent et `CTimeSpan` soustraisent `CTime` un objet à cet objet et à partir de celui-ci.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
L’objet `CTimeSpan` à ajouter ou à soustraire.

### <a name="return-value"></a>Valeur de retour

L’objet mis à jour. `CTime`

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire un `CTimeSpan` objet à et à partir de cet `CTime` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a>CTime::Serialize64

> [!NOTE]
> Cette méthode n’est disponible que dans les projets MFC.

Sérialise les données associées à la variable du membre vers ou depuis une archive.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
L’objet `CArchive` que vous souhaitez mettre à jour.

### <a name="return-value"></a>Valeur de retour

L’objet mis à jour. `CArchive`

## <a name="see-also"></a>Voir aussi

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Classe CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
