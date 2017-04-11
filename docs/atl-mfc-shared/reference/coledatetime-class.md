---
title: Classe COleDateTime | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 2b4e8709da1287e4e33e51606df7f544761b0b54
ms.lasthandoff: 04/04/2017

---
# <a name="coledatetime-class"></a>COleDateTime (classe)
Encapsule la `DATE` type de données qui est utilisé dans OLE automation.  
  
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
|[COleDateTime::Format](#format)|Génère une représentation sous forme de chaîne mise en forme d’un `COleDateTime` objet.|  
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` de l’objet en un **DBTIMESTAMP** structure de données.|  
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` de l’objet en un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure de données.|  
|[COleDateTime::GetAsUDATE](#getasudate)|Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` comme un **UDATE** structure de données.|  
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Crée un `COleDateTime` objet qui représente l’heure actuelle (fonction membre statique).|  
|[COleDateTime::GetDay](#getday)|Retourne le jour cela `COleDateTime` objet représente (1 à 31).|  
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Retourne le jour de la semaine cela `COleDateTime` objet représente (dimanche = 1).|  
|[COleDateTime::GetDayOfYear](#getdayofyear)|Retourne le jour de l’année cette `COleDateTime` objet représente (Jan 1 = 1).|  
|[COleDateTime::GetHour](#gethour)|Retourne l’heure cela `COleDateTime` représente l’objet (0 - 23).|  
|[COleDateTime::GetMinute](#getminute)|Retourne la minute cela `COleDateTime` représente l’objet (0 - 59).|  
|[COleDateTime::GetMonth](#getmonth)|Retourne le mois cette `COleDateTime` objet représente (1-12).|  
|[COleDateTime::GetSecond](#getsecond)|Retourne la deuxième cette `COleDateTime` représente l’objet (0 - 59).|  
|[COleDateTime::GetStatus](#getstatus)|Obtient l’état (validité) de ce `COleDateTime` objet.|  
|[COleDateTime::GetYear](#getyear)|Retourne l’année cette `COleDateTime` représente l’objet.|  
|[COleDateTime::ParseDateTime](#parsedatetime)|Lit une valeur de date/heure dans une chaîne et définit la valeur de `COleDateTime`.|  
|[COleDateTime::SetDate](#setdate)|Définit la valeur de cet `COleDateTime` objet à la valeur de date uniquement spécifiée.|  
|[COleDateTime::SetDateTime](#setdatetime)|Définit la valeur de cet `COleDateTime` objet à la valeur de date/heure spécifiée.|  
|[COleDateTime::SetStatus](#setstatus)|Définit l’état (validité) de ce `COleDateTime` objet.|  
|[COleDateTime::SetTime](#settime)|Définit la valeur de cet `COleDateTime` objet à la valeur spécifiée de l’exécution uniquement.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  

|Nom|Description|  
|----------|-----------------|  
|[Rubrique COleDateTime::opérateur ==, rubrique COleDateTime::opérateur<,></,>](#coledatetime_relational_operators)|Comparer deux `COleDateTime` valeurs.|  
|[Rubrique COleDateTime::opérateur +, rubrique COleDateTime::opérateur-](#operator_add_-)|Ajouter ou soustraire `COleDateTime` valeurs.|  
|[Rubrique COleDateTime::opérateur +=, rubrique COleDateTime::opérateur =](#operator_add_eq_-_eq)|Ajouter ou soustraire un `COleDateTime` valeur à partir de ce `COleDateTime` objet.|  
|[Rubrique COleDateTime::opérateur =](#operator_eq)|Copie un `COleDateTime` valeur.|  
|[Rubrique COleDateTime::opérateur DATE, Date de la rubrique COleDateTime::opérateur *](#operator_date)|Convertit un `COleDateTime` valeur dans un `DATE` ou `DATE*`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDateTime::m_dt](#m_dt)|Contient l’objet sous-jacent **DATE** pour ce `COleDateTime` objet.|  
|[COleDateTime::m_status](#m_status)|Contient l’état de ce `COleDateTime` objet.|  
  
## <a name="remarks"></a>Remarques  
 `COleDateTime`ne dispose pas d’une classe de base.  
  
 C’est un des types possibles pour le [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) type de données d’OLE automation. A `COleDateTime` valeur représente une date absolue et la valeur d’heure.  
  
 Le `DATE` type est implémenté en tant que valeur à virgule flottante. Jours sont mesurées du 30 décembre 1899 à minuit. Le tableau suivant présente certaines dates et leurs valeurs associées :  
  
|Date|Valeur|  
|----------|-----------|  
|29 décembre 1899, minuit|-1.0|  
|29 décembre 1899, 6 h|-1.25|  
|Le 30 décembre 1899, minuit|0.0|  
|Le 31 décembre 1899, minuit|1.0|  
|1er janvier 1900, 6 h 00|2.25|  
  
> [!CAUTION]
>  Dans le tableau ci-dessus, notez que bien que les valeurs de jour deviennent négatifs avant le 30 décembre 1899 à minuit heure des valeurs ne le font pas. Par exemple, 6:00 AM est toujours représentée par une valeur fractionnaire 0,25 que l’entier représentant le jour soit positive (après le 30 décembre 1899) ou négatif (avant le 30 décembre 1899). Cela signifie qu’une simple comparaison point flottante triez par erreur un `COleDateTime` représentant 6 h 00 29/12/1899 en tant que **ultérieurement** à un représentant 7 h 00 le jour même.  
  
 La `COleDateTime` classe gère les dates comprises entre le 1er janvier 100 et le 31 décembre 9999. La `COleDateTime` classe utilise le calendrier grégorien ; il ne prend pas en charge les dates juliennes. `COleDateTime`ignore l’heure d’été. (Consultez [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).)  
  
> [!NOTE]
>  Vous pouvez utiliser la `%y` format pour récupérer une année à deux chiffres que pour les dates en commençant à 1900. Si vous utilisez la `%y` format sur une date antérieure à 1900, le code génère un échec d’assertion.  
  
 Ce type est également utilisé pour représenter les valeurs de date uniquement ou uniquement. Par convention, la date 0 (30 décembre 1899) est utilisée pour les valeurs d’heure uniquement, et l’heure 00:00 (minuit) est utilisé pour les valeurs de date uniquement.  
  
 Si vous créez un `COleDateTime` objet à l’aide d’une date inférieure à 100, la date est acceptées, mais les appels ultérieurs à `GetYear`, `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, et `GetSecond` échouent et retournent -1. Auparavant, vous pouvez utiliser les dates à deux chiffres, mais les dates doivent être 100 ou supérieure dans MFC 4.2 et versions ultérieures.  
  
 Pour éviter tout problème, spécifiez une date à quatre chiffres. Exemple :  
  
 [!code-cpp[NVC_ATLMFC_Utilities n° 1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]  
  
 Opérations arithmétiques de base pour le `COleDateTime` valeurs utilisent la classe compagnon [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`valeurs définissent un intervalle de temps. La relation entre ces classes est similaire à celle entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Pour plus d’informations sur la `COleDateTime` et `COleDateTimeSpan` des classes, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="requirements"></a>Spécifications  
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
 `date`  
 Le **COleDateTime** objet à comparer.  
  
### <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Un ATLASSERT ; se produit si une des deux opérandes n’est pas valide.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]  
  
### <a name="example"></a>Exemple  
 The operators **>=**, **\<=**, **>**, and **<**, will assert if the `COleDateTime` object is set to null.  
  
 [!code-cpp[NVC_ATLMFC_Utilities #170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]  
  
##  <a name="coledatetime"></a>COleDateTime::COleDateTime  
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
COleDateTime(const DBTIMESTAMP& dbts) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `dateSrc`  
 Existant `COleDateTime` à copier dans le nouvel objet `COleDateTime` objet.  
  
 *varSrc*  
 Existant **VARIANT** structure de données (éventuellement un `COleVariant` objet) à convertir en une valeur date/heure ( `VT_DATE`) et le copier dans le nouvel `COleDateTime` objet.  
  
 `dtSrc`  
 Une date/heure ( **DATE**) valeur à copier dans le nouvel `COleDateTime` objet.  
  
 `timeSrc`  
 A `time_t` ou **__time64_t** valeur convertie en valeur de date/heure et la copie dans le nouvel `COleDateTime` objet.  
  
 *systimeSrc*  
 A `SYSTEMTIME` structure à être convertie en valeur de date/heure et copiés dans le nouvel `COleDateTime` objet.  
  
 `filetimeSrc`  
 A `FILETIME` structure à être convertie en valeur de date/heure et copiés dans le nouvel `COleDateTime` objet. Notez que `FILETIME` utilise le temps universel coordonné (UTC), donc, si vous passez une heure locale de la structure, vos résultats seront incorrects. Consultez [fichier fois](http://msdn.microsoft.com/library/windows/desktop/ms724290) dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] pour plus d’informations.  
  
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Indiquer les valeurs de date et d’heure doit être copié dans le nouvel `COleDateTime` objet.  
  
 `wDosDate`, `wDosTime`  
 Valeurs de date et heure MS-DOS convertie en valeur de date/heure et la copie dans le nouvel `COleDateTime` objet.  
  
 `dbts`  
 Une référence à un [DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) structure qui contient l’heure locale actuelle.  
  
### <a name="remarks"></a>Notes  
 Créent tous les constructeurs de ces `COleDateTime` objet initialisé à la valeur spécifiée. Le tableau suivant présente les plages valides pour chaque composant de date et d’heure :  
  
|Composant de date/heure|Plage valide|  
|--------------------------|-----------------|  
|année|100 - 9999|  
|mois|0 - 12|  
|jour|0 - 31|  
|heure|0 - 23|  
|minute|0 - 59|  
|second|0 - 59|  
  
 Notez que la limite supérieure réelle pour le composant de jour varie en fonction des composants mois et année. Pour plus d’informations, consultez la **SetDate** ou `SetDateTime` fonctions membres.  
  
 Voici une brève description de chaque constructeur :  
  
- `COleDateTime(`**)** Construit un `COleDateTime` objet initialisé à 0 (30 décembre 1899, minuit).  
  
- `COleDateTime(``dateSrc` **)** Construit un `COleDateTime` objet d’un existant `COleDateTime` objet.  
  
- `COleDateTime(`*varSrc* **)** construit un `COleDateTime` objet. Tente de convertir un `VARIANT` structure ou [COleVariant](../../mfc/reference/colevariant-class.md) objet à une date/heure ( `VT_DATE`) valeur. Si cette conversion réussit, la valeur convertie est copiée dans le nouvel `COleDateTime` objet. Si elle n’est pas le cas, la valeur de la `COleDateTime` objet a la valeur 0 (30 décembre 1899, minuit) et son état non valide.  
  
- `COleDateTime(``dtSrc` **)** Construit un `COleDateTime` de l’objet d’un **DATE** valeur.  
  
- `COleDateTime(``timeSrc` **)** Construit un `COleDateTime` de l’objet d’un `time_t` valeur.  
  
- `COleDateTime(`*systimeSrc* **)** construit un `COleDateTime` de l’objet d’un `SYSTEMTIME` valeur.  
  
- `COleDateTime(``filetimeSrc` **)** Construit un `COleDateTime` de l’objet d’un `FILETIME` valeur. . Notez que `FILETIME` utilise le temps universel coordonné (UTC), donc, si vous passez une heure locale de la structure, vos résultats seront incorrects. Consultez [fichier fois](http://msdn.microsoft.com/library/windows/desktop/ms724290) dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] pour plus d’informations.  
  
- `COleDateTime(``nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec` **)** Construit un `COleDateTime` objet à partir de le des valeurs numériques spécifiées.  
  
- `COleDateTime(``wDosDate`, `wDosTime` **)** Construit un `COleDateTime` objet à partir des valeurs de date et heure de MS-DOS spécifiés.  
  
 Pour plus d’informations sur la `time_t` de type de données, consultez la [temps](../../c-runtime-library/reference/time-time32-time64.md) de fonction dans le *Run-Time Library Reference*.  
  
 Pour plus d’informations, consultez la [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) et [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) structures dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
> [!NOTE]
>  Le constructeur à l’aide de **DBTIMESTAMP** paramètre n’est disponible que lorsque OLEDB.h est inclus.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]  
  
##  <a name="format"></a>COleDateTime::Format  
 Crée une représentation sous forme de mise en forme de la valeur de date/heure.  
  
```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 Indique un des indicateurs de paramètres régionaux suivants :  
  
- `LOCALE_NOUSEROVERRIDE`Utilisez les paramètres régionaux par défaut du système, au lieu des paramètres utilisateur personnalisés.  
  
- `VAR_TIMEVALUEONLY`Ignorer la partie date lors de l’analyse.  
  
- `VAR_DATEVALUEONLY`Ignorer la partie heure lors de l’analyse.  
  
 `lcid`  
 Indique l’ID de paramètres régionaux à utiliser pour la conversion. Pour plus d’informations sur les identificateurs de langue, consultez [des identificateurs de langue](http://msdn.microsoft.com/library/windows/desktop/dd318691).  
  
 `lpszFormat`  
 Une mise en forme de chaîne similaire à la `printf` mise en forme de chaîne. Chaque mise en forme de code, précédé d’un pourcentage ( `%`) se connecter, est remplacé par le correspondant `COleDateTime` composant. Autres caractères dans la chaîne de mise en forme sont copiés sans modification à la chaîne retournée. Reportez-vous à la fonction runtime [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour plus d’informations. La valeur et la signification des codes de mise en forme pour `Format` sont :  
  
- `%H`Heures du jour actuel  
  
- `%M`Minutes à l’heure actuelle  
  
- `%S`Secondes dans la minute en cours  
  
- `%%`Symbole de pourcentage  
  
 `nFormatID`  
 L’ID de ressource pour la chaîne de format de contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient la valeur de date/heure de mise en forme.  
  
### <a name="remarks"></a>Notes  
 Si l’état de ce `COleDateTime` objet est null, la valeur de retour est une chaîne vide. Si l’état n’est pas valide, la chaîne de retour est spécifiée par la ressource de chaîne `ATL_IDS_DATETIME_INVALID`.  
  
 Une brève description des trois formes pour cette fonction suit :  
  
 `Format`( `dwFlags`, `lcid`)  
 Ce formulaire met en forme la valeur en utilisant les spécifications de langue (ID de paramètres régionaux) pour la date et l’heure. À l’aide des paramètres par défaut, cet écran s’impriment la date et l’heure, sauf si la partie heure est 0 (minuit), auquel cas il va imprimer uniquement la date, ou la partie date est 0 (30 décembre 1899) dans auquel cas il imprime le temps. Si la valeur de date/heure est 0 (30 décembre 1899, minuit), ce formulaire avec les paramètres par défaut s’imprime à minuit.  
  
 `Format`( `lpszFormat`)  
 Ce formulaire met en forme la valeur à l’aide de la chaîne de format qui contient les codes de mise en forme spéciale qui sont précédés d’un signe de pourcentage (%), comme dans `printf`. La chaîne mise en forme est passée en tant que paramètre à la fonction. Pour plus d’informations sur les codes de mise en forme, consultez [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans la référence de la bibliothèque Runtime.  
  
 `Format`( `nFormatID`)  
 Ce formulaire met en forme la valeur à l’aide de la chaîne de format qui contient les codes de mise en forme spéciale qui sont précédés d’un signe de pourcentage (%), comme dans `printf`. La chaîne mise en forme est une ressource. L’ID de ressource de cette chaîne est passée comme paramètre. Pour plus d’informations sur les codes de mise en forme, consultez [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dans les *Run-Time Library Reference*.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities n° 3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]  
  
##  <a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP  
 Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` de l’objet en un **DBTIMESTAMP** structure de données.  
  
```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `dbts`  
 Une référence à un [DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Remarques  
 Stocke l'heure résultante dans la structure `dbts` référencée. Le **DBTIMESTAMP** structure de données initialisée par cette fonction aura son **fraction** membre défini à zéro.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]  
  
##  <a name="getassystemtime"></a>COleDateTime::GetAsSystemTime  
 Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` de l’objet en un `SYSTEMTIME` structure de données.  
  
```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *sysTime*  
 Une référence à un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure pour recevoir la valeur de date/heure convertie à partir de la `COleDateTime` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** en cas de réussite ; **false** si la conversion échoue, ou si le `COleDateTime` objet est **NULL** ou non valide.  
  
### <a name="remarks"></a>Notes  
 `GetAsSystemTime`stocke l’heure résultante dans référencé *sysTime* objet. Le `SYSTEMTIME` structure de données initialisée par cette fonction aura son **wMilliseconds** membre défini à zéro.  
  
 Consultez [GetStatus](#getstatus) pour plus d’informations sur les informations d’état contenues dans un `COleDateTime` objet.  
  
##  <a name="getasudate"></a>COleDateTime::GetAsUDATE  
 Appelez cette méthode pour obtenir l’heure dans le `COleDateTime` de l’objet en un **UDATE** structure de données.  
  
```
bool GetAsUDATE(UDATE& udate) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `udate`  
 Une référence à un **UDATE** structure pour recevoir la valeur de date/heure convertie à partir de la `COleDateTime` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** en cas de réussite ; **false** si la conversion échoue, ou si le `COleDateTime` objet est **NULL** ou non valide.  
  
### <a name="remarks"></a>Remarques  
 A **UDATE** structure représente une date de « décompressée ».  
  
##  <a name="getcurrenttime"></a>COleDateTime::GetCurrentTime  
 Appelez cette fonction membre statique pour retourner la valeur de date/heure actuelle.  
  
```
static COleDateTime WINAPI GetCurrentTime() throw();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities n ° 5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]  
  
##  <a name="getday"></a>COleDateTime::GetDay  
 Obtient le jour du mois représenté par cette valeur de date/heure.  
  
```
int GetDay() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le jour du mois représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour n’a pas pu être obtenu.  
  
### <a name="remarks"></a>Remarques  
 Plage de valeurs de retour valide compris entre 1 et 31.  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities n° 6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]  
  
##  <a name="getdayofweek"></a>COleDateTime::GetDayOfWeek  
 Obtient le jour du mois représenté par cette valeur de date/heure.  
  
```
int GetDayOfWeek() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le jour de semaine représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour de la semaine n’a pas pu être obtenu.  
  
### <a name="remarks"></a>Notes  
 Les valeurs de retour valide compris entre 1 et 7, où 1 = dimanche, 2 = lundi et ainsi de suite.  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]  
  
##  <a name="getdayofyear"></a>COleDateTime::GetDayOfYear  
 Obtient le jour de l’année représenté par cette valeur de date/heure.  
  
```
int GetDayOfYear() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le jour de l’année représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le jour de l’année n’a pas pu être obtenu.  
  
### <a name="remarks"></a>Remarques  
 Retour valide les valeurs sont comprises entre 1 et 366, où le 1er janvier = 1.  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]  
  
##  <a name="gethour"></a>COleDateTime::GetHour  
 Obtient l’heure représentée par cette valeur de date/heure.  
  
```
int GetHour() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’heure représentée par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si l’heure n’a pas pu être obtenue.  
  
### <a name="remarks"></a>Remarques  
 Plage de valeurs de retour valide comprise entre 0 et 23.  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]  
  
##  <a name="getminute"></a>COleDateTime::GetMinute  
 Obtient la minute représentée par cette valeur de date/heure.  
  
```
int GetMinute() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La minute représentée par la valeur de ce `COleDateTime` objet ou `COleDateTime::error` si la minute n’a pas pu être obtenue.  
  
### <a name="remarks"></a>Remarques  
 Plage de valeurs de retour valide comprise entre 0 et 59.  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetHour](#gethour).  
  
##  <a name="getmonth"></a>COleDateTime::GetMonth  
 Obtient le mois représenté par cette valeur de date/heure.  
  
```
int GetMonth() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Mois représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si le mois n’a pas pu être obtenu.  
  
### <a name="remarks"></a>Remarques  
 Plage de valeurs de retour valide compris entre 1 et 12.  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetDay](#getday).  
  
##  <a name="getsecond"></a>COleDateTime::GetSecond  
 Obtient la deuxième représentée par cette valeur de date/heure.  
  
```
int GetSecond() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La seconde représentée par la valeur de ce `COleDateTime` objet ou `COleDateTime::error` si la seconde n’a pas pu être obtenue.  
  
### <a name="remarks"></a>Remarques  
 Plage de valeurs de retour valide comprise entre 0 et 59.  
  
> [!NOTE]
>  La `COleDateTime` classe ne prend pas en charge les secondes intercalaires.  
  
 Pour plus d’informations sur l’implémentation de `COleDateTime`, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetHour](#gethour).  
  
##  <a name="getstatus"></a>COleDateTime::GetStatus  
 Obtient l’état (validité) d’une donnée `COleDateTime` objet.  
  
```
DateTimeStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’état de ce `COleDateTime` valeur. Si vous appelez **GetStatus** sur un `COleDateTime` objet construit avec la valeur par défaut, elle retournera valide. Si vous appelez **GetStatus** sur un `COleDateTime` objet initialisé avec la constructeur a la valeur null, **GetStatus** retourne la valeur null. Consultez **remarques** pour plus d’informations.  
  
### <a name="remarks"></a>Remarques  
 La valeur de retour est définie par le **DateTimeStatus** type énuméré, qui est défini dans la `COleDateTime` classe.  
  
```  
enum DateTimeStatus  
{  
   error = -1,  
   valid = 0,  
   invalid = 1,    // Invalid date (out of range, etc.)  
   null = 2,       // Literally has no value  
};  
```  
  
 Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :  
  
- `COleDateTime::error`Indique qu’une erreur s’est produite lors de la tentative d’obtention de partie de la valeur de date/heure.  
  
- **COleDateTime::valid** indique que cette `COleDateTime` objet est valide.  
  
- **COleDateTime::invalid** indique que cette `COleDateTime` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.  
  
- **COleDateTime::null** indique que cette `COleDateTime` objet est null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « null » dans le sens de la base de données de « aucune valeur, les clauses having » plutôt que de C++ **NULL**.)  
  
 L’état d’un `COleDateTime` objet n’est pas valide dans les cas suivants :  
  
-   Si sa valeur est définie à partir d’un **VARIANT** ou `COleVariant` valeur qui n’a pas pu être convertie en une valeur date/heure.  
  
-   Si sa valeur est définie à partir d’un `time_t`, `SYSTEMTIME`, ou `FILETIME` valeur qui n’a pas pu être convertie en une valeur de date/heure valide.  
  
-   Si sa valeur est définie par `SetDateTime` avec des valeurs de paramètre non valide.  
  
-   Si cet objet a rencontré un dépassement de capacité positif ou négatif pendant une opération arithmétique d’assignation, à savoir, `+=` ou `-=`.  
  
-   Si une valeur non valide a été assignée à cet objet.  
  
-   Si l’état de cet objet a été explicitement défini non valide à l’aide de `SetStatus`.  
  
 Pour plus d’informations sur les opérations qui peuvent définir l’état non valide, consultez les fonctions membres suivantes :  
  
- [COleDateTime](#coledatetime)  
  
- [SetDateTime](#setdatetime)  
  
- [opérateur +, -](#operator_add_-)  
  
- [+= (opérateur)-=](#operator_add_eq_-_eq)  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]  
  
##  <a name="getyear"></a>COleDateTime::GetYear  
 Obtient l’année représenté par cette valeur de date/heure.  
  
```
int GetYear() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’année représenté par la valeur de cet `COleDateTime` objet ou `COleDateTime::error` si l’année n’a pas pu être obtenue.  
  
### <a name="remarks"></a>Remarques  
 Plage de valeurs de retour valide comprise entre 100 et 9999, qui inclut le siècle.  
  
 Pour plus d’informations sur les autres fonctions membres qui interrogent la valeur de cette `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetDay](#getday).  
  
##  <a name="m_dt"></a>COleDateTime::m_dt  
 Sous-jacent **DATE** structure pour ce `COleDateTime` objet.  
  
```
DATE m_dt;
```  
  
### <a name="remarks"></a>Remarques  
  
> [!CAUTION]
>  Modification de la valeur dans la **DATE** accédé par le pointeur retourné par cette fonction modifie la valeur de cet `COleDateTime` objet. Il ne modifie pas l’état de ce `COleDateTime` objet.  
  
 Pour plus d’informations sur l’implémentation de la **DATE** d’objets, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="m_status"></a>COleDateTime::m_status  
 Contient l’état de ce `COleDateTime` objet.  
  
```
DateTimeStatus m_status;
```  
  
### <a name="remarks"></a>Remarques  
 Le type de ce membre de données est le type énuméré **DateTimeStatus**, qui est défini dans la `COleDateTime` classe. Consultez [COleDateTime::GetStatus](#getstatus) pour plus d’informations.  
  
> [!CAUTION]
>  Ce membre de données concerne les situations de programmation avancées. Vous devez utiliser les fonctions de membre inline [GetStatus](#getstatus) et [SetStatus](#setstatus). Consultez `SetStatus` pour les autres avertissements concernant la définition explicite de ce membre de données.  
  
##  <a name="operator_eq"></a>Rubrique COleDateTime::opérateur =  
 Copie un `COleDateTime` valeur.  
  
```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& udate) throw();
```  
  
### <a name="remarks"></a>Notes  
 Ces opérateurs d’assignation surchargés copiez la valeur de date/heure source dans cette `COleDateTime` objet. Une brève description de chacune de ces surchargée suit d’opérateurs d’assignation :  
  
- **opérateur = (** `dateSrc` **)** la valeur et l’état de l’opérande sont copiés dans ce `COleDateTime` objet.  
  
- **opérateur = (** *varSrc* **)** si la conversion de la [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) valeur (ou [COleVariant](../../mfc/reference/colevariant-class.md) objet) à une date/heure ( `VT_DATE`) est réussie, la valeur convertie est copiée dans ce `COleDateTime` objet et son état est défini à valide. Si la conversion n’a pas réussie, la valeur de cet objet est définie à zéro (30 décembre 1899, minuit) et son état non valide.  
  
- **opérateur = (** `dtSrc` **)** le **DATE** valeur est copiée dans ce `COleDateTime` objet et son état est défini à valide.  
  
- **opérateur = (** `timeSrc` **)** le `time_t` ou **__time64_t** valeur est convertie et copié dans ce `COleDateTime` objet. Si la conversion est réussie, l’état de cet objet est défini sur valide. Si échoue, il est défini à non valide.  
  
- **opérateur = (** *systimeSrc* **)** le [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) valeur est convertie et copié dans ce `COleDateTime` objet. Si la conversion est réussie, l’état de cet objet est défini sur valide. Si échoue, il est défini à non valide.  
  
- **opérateur = (** `udate` **)** le **UDATE** valeur est convertie et copié dans ce `COleDateTime` objet. Si la conversion est réussie, l’état de cet objet est défini sur valide. Si échoue, il est défini à non valide. A **UDATE** structure représente une date de « décompressée ». Consultez la fonction [VarDateFromUdate](http://msdn.microsoft.com/en-us/1c924ac5-b896-49e1-9ccf-825ac7a030c8) pour plus d’informations.  
  
- **opérateur = (** `filetimeSrc` **)** le [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) valeur est convertie et copié dans ce `COleDateTime` objet. Si la conversion est réussie, l’état de cet objet est défini sur valide. dans le cas contraire, elle est définie à non valide. `FILETIME`utilise temps universel coordonné (UTC), si vous passez une heure UTC dans la structure, vos résultats seront converties à partir de l’heure UTC en heure locale et seront stockées en tant que variante temporelle. Ce comportement est le même que dans Visual C++ 6.0 et Visual C++ .NET 2003 SP2. Consultez [fichier fois](http://msdn.microsoft.com/library/windows/desktop/ms724290) dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] pour plus d’informations.  
  
 Pour plus d’informations, consultez la [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) entrée dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations sur la `time_t` de type de données, consultez la [temps](../../c-runtime-library/reference/time-time32-time64.md) de fonction dans le *Run-Time Library Reference*.  
  
 Pour plus d’informations, consultez la [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) et [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) structures dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_add_-"></a>Rubrique COleDateTime::opérateur +, -  
 Ajouter ou soustraire **ColeDateTime** valeurs.  
  
```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```  
  
### <a name="remarks"></a>Remarques  
 `COleDateTime`objets représentent les heures absolues. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) objets représentent les heures relatifs. Les deux premiers opérateurs permettent d’ajouter ou soustraire un `COleDateTimeSpan` valeur un `COleDateTime` valeur. Le troisième opérateur vous permet de soustraire un `COleDateTime` valeur d’une autre pour produire un `COleDateTimeSpan` valeur.  
  
 Si un des opérandes est null, l’état de la `COleDateTime` la valeur est null.  
  
 Si résultant `COleDateTime` valeur se situe en dehors des limites de valeurs acceptables, l’état de ce `COleDateTime` valeur n’est pas valide.  
  
 Si un des opérandes n’est pas valide et que l’autre n’est pas null, l’état des résultats de `COleDateTime` valeur n’est pas valide.  
  
 Le **+** et **-** opérateurs vérifie si le `COleDateTime` objet est défini avec la valeur null. Consultez [les opérateurs relationnels COleDateTime](#coledatetime_relational_operators) pour obtenir un exemple.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>Rubrique COleDateTime::opérateur +=-=  
 Ajouter ou soustraire un **ColeDateTime** valeur à partir de ce `COleDateTime` objet.  
  
```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>Remarques  
 Ces opérateurs permettent d’ajouter ou soustraire un `COleDateTimeSpan` valeur vers et à partir de ce `COleDateTime`. Si un des opérandes est null, l’état de la `COleDateTime` la valeur est null.  
  
 Si résultant `COleDateTime` valeur se situe en dehors des limites de valeurs acceptables, l’état de ce `COleDateTime` a la valeur à non valide.  
  
 Si un des opérandes n’est pas valide et l’autre n’est pas null, l’état des résultats de `COleDateTime` valeur n’est pas valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
 Le **+=** et **-=** opérateurs vérifie si le `COleDateTime` objet est défini avec la valeur null. Consultez [les opérateurs relationnels COleDateTime](#coledatetime_relational_operators) pour obtenir un exemple.  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_date"></a>Rubrique COleDateTime::opérateur DATE  
 Convertit un **ColeDateTime** valeur dans un **DATE**.  
  
```
operator DATE() const throw();
```  
  
### <a name="remarks"></a>Remarques  
 Cet opérateur retourne un **DATE** objet dont la valeur est copiée à partir de ce `COleDateTime` objet. Pour plus d’informations sur l’implémentation de la **DATE** d’objets, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
 Le **DATE** opérateur vérifie si le `COleDateTime` objet est défini avec la valeur null. Consultez [les opérateurs relationnels COleDateTime](#coledatetime_relational_operators) pour obtenir un exemple.  
  
##  <a name="parsedatetime"></a>COleDateTime::ParseDateTime  
 Analyse une chaîne pour lire une valeur de date/heure.  
  
```
bool ParseDateTime(  
 LPCTSTR lpszDate,
 DWORD dwFlags = 0,
 LCID lcid = LANG_USER_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszDate`  
 Pointeur vers la chaîne se terminant par null qui doit être analysé. Pour plus d'informations, consultez Notes.  
  
 `dwFlags`  
 Indique les indicateurs de paramètres régionaux et de l’analyse. Un ou plusieurs des indicateurs suivants :  
  
- **LOCALE_NOUSEROVERRIDE** utiliser des paramètres régionaux par défaut du système, au lieu des paramètres utilisateur personnalisés.  
  
- **VAR_TIMEVALUEONLY** ignorer la partie date lors de l’analyse.  
  
- **VAR_DATEVALUEONLY** ignorer la partie heure lors de l’analyse.  
  
 `lcid`  
 Indique l’ID de paramètres régionaux à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si la chaîne a été correctement convertie en valeur de date/heure, sinon **false**.  
  
### <a name="remarks"></a>Notes  
 Si la chaîne a été correctement convertie en une date/heure de valeur, la valeur de cet `COleDateTime` objet est défini pour cette valeur et son état valide.  
  
> [!NOTE]
>  Les valeurs d’année doivent être comprises entre 100 et 9999, inclus.  
  
 Le `lpszDate` paramètre peut prendre une variété de formats. Par exemple, les chaînes suivantes contiennent des formats de date/heure acceptable :  
  
 `"25 January 1996"`  
  
 `"8:30:00"`  
  
 `"20:30:00"`  
  
 `"January 25, 1996 8:30:00"`  
  
 `"8:30:00 Jan. 25, 1996"`  
  
 `"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`  
  
 Notez que l’ID de paramètres régionaux affectent également si le format de chaîne est acceptable pour la conversion en une valeur date/heure.  
  
 Dans le cas de **VAR_DATEVALUEONLY**, l’heure a la valeur heure 0 ou minuit. Dans le cas de **VAR_TIMEVALUEONLY**, la date a la valeur date 0, ce qui signifie le 30 décembre 1899.  
  
 Si la chaîne n’a pas pu être convertie en valeur de date/heure ou s’il existe un dépassement de capacité numérique, l’état de ce `COleDateTime` objet n’est pas valide.  
  
 Pour plus d’informations sur les limites et la mise en œuvre pour `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="setdate"></a>COleDateTime::SetDate  
 Définit la date de ce `COleDateTime` objet.  
  
```
int SetDate(  
 int nYear,
 int nMonth,
 int nDay) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nYear`, `nMonth`, `nDay`  
 Indiquer les composants de date doit être copié dans ce `COleDateTime` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Zéro si la valeur de cet `COleDateTime` objet a été défini avec succès ; sinon, 1. Cette valeur de retour est basée sur le **DateTimeStatus** type énuméré. Pour plus d’informations, consultez la [SetStatus](#setstatus) fonction membre.  
  
### <a name="remarks"></a>Remarques  
 La date est définie pour les valeurs spécifiées. L’heure est définie à l’heure 0, minuit.  
  
 Consultez le tableau suivant pour les limites pour les valeurs de paramètre :  
  
|Paramètre|Limites|  
|---------------|------------|  
|`nYear`|100 - 9999|  
|`nMonth`|1 - 12|  
|`nDay`|0 - 31|  
  
 Si le jour du mois dépasse, il est converti au jour du mois suivant et le mois correct et/ou année est incrémentée en conséquence. Une valeur de jour de zéro indique le dernier jour du mois précédent. Le comportement est identique à `SystemTimeToVariantTime`.  
  
 Si la valeur de date spécifiée par les paramètres n’est pas valide, l’état de cet objet est défini sur **COleDateTime::invalid**. Vous devez utiliser [GetStatus](#getstatus) pour vérifier la validité de la **DATE** valeur et ne doit pas supposer que la valeur de [m_dt](#m_dt) ne seront pas modifiés.  
  
 Voici quelques exemples de valeurs de date :  
  
|`nYear`|`nMonth`|`nDay`|Valeur|  
|-------------|--------------|------------|-----------|  
|2000|2|29|29 février 2000|  
|1776|7|4|4 juillet 1776|  
|1925|4|35|35 avril 1925 (date non valide)|  
|10000|1|1|1er janvier 10000 (date non valide)|  
  
 Pour définir la date et heure, consultez [COleDateTime::SetDateTime](#setdatetime).  
  
 Pour plus d’informations sur les fonctions membres qui interrogent la valeur de cet `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATLMFC_Utilities #11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]  
  
##  <a name="setdatetime"></a>COleDateTime::SetDateTime  
 Définit la date et l’heure de ce `COleDateTime` objet.  
  
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
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Indiquer les composants de date et d’heure doit être copié dans ce `COleDateTime` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Zéro si la valeur de cet `COleDateTime` objet a été défini avec succès ; sinon, 1. Cette valeur de retour est basée sur le **DateTimeStatus** type énuméré. Pour plus d’informations, consultez la [SetStatus](#setstatus) fonction membre.  
  
### <a name="remarks"></a>Notes  
 Consultez le tableau suivant pour les limites pour les valeurs de paramètre :  
  
|Paramètre|Limites|  
|---------------|------------|  
|`nYear`|100 - 9999|  
|`nMonth`|1 - 12|  
|`nDay`|0 - 31|  
|`nHour`|0 - 23|  
|`nMin`|0 - 59|  
|`nSec`|0 - 59|  
  
 Si le jour du mois dépasse, il est converti au jour du mois suivant et le mois correct et/ou année est incrémentée en conséquence. Une valeur de jour de zéro indique le dernier jour du mois précédent. Le comportement est identique à [SystemTimeToVariantTime](http://msdn.microsoft.com/en-us/d9d69521-9b33-4fc5-8a1c-929f216db450).  
  
 Si la valeur de date ou heure spécifiée par les paramètres n’est pas valide, que l’état de cet objet a la valeur non valide et la valeur de cet objet n’est pas modifiée.  
  
 Voici quelques exemples de valeurs d’heure :  
  
|`nHour`|`nMin`|`nSec`|Valeur|  
|-------------|------------|------------|-----------|  
|1|3|3|01:03:03|  
|23|45|0|23:45:00|  
|25|30|0|Non valide|  
|9|60|0|Non valide|  
  
 Voici quelques exemples de valeurs de date :  
  
|`nYear`|`nMonth`|`nDay`|Valeur|  
|-------------|--------------|------------|-----------|  
|1995|4|15|15 avril 1995|  
|1789|7|14|17 juillet 1789|  
|1925|2|30|Non valide|  
|10000|1|1|Non valide|  
  
 Pour définir la date uniquement, consultez [COleDateTime::SetDate](#setdate). Pour définir uniquement l’heure, consultez [COleDateTime::SetTime](#settime).  
  
 Pour plus d’informations sur les fonctions membres qui interrogent la valeur de cet `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetStatus](#getstatus).  
  
##  <a name="setstatus"></a>COleDateTime::SetStatus  
 Définit l’état de ce `COleDateTime` objet.  
  
```
void SetStatus(DateTimeStatus status) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *status*  
 La nouvelle valeur pour ce `COleDateTime` objet.  
  
### <a name="remarks"></a>Remarques  
 Le *état* la valeur du paramètre est définie par le **DateTimeStatus** type énuméré, qui est défini dans la `COleDateTime` classe. Consultez [COleDateTime::GetStatus](#getstatus) pour plus d’informations.  
  
> [!CAUTION]
>  Cette fonction concerne les situations de programmation avancées. Cette fonction ne modifie pas les données dans cet objet. Il servira plus souvent à définir l’état à `null` ou **non valide**. Notez que l’opérateur d’assignation ( [opérateur =](#eq)) et [SetDateTime](#setdatetime) ne définissez pas l’état de l’objet basé sur les valeurs de la source.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetStatus](#getstatus).  
  
##  <a name="settime"></a>COleDateTime::SetTime  
 Définit l’heure de cette `COleDateTime` objet.  
  
```
int SetTime(  
 int nHour,
 int nMin,
 int nSec) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nHour`, `nMin`, `nSec`  
 Indiquer les composants heure doit être copié dans ce `COleDateTime` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Zéro si la valeur de cet `COleDateTime` objet a été défini avec succès ; sinon, 1. Cette valeur de retour est basée sur le **DateTimeStatus** type énuméré. Pour plus d’informations, consultez la [SetStatus](#setstatus) fonction membre.  
  
### <a name="remarks"></a>Notes  
 L’heure est définie pour les valeurs spécifiées. La date est définie à la date 0, ce qui signifie le 30 décembre 1899.  
  
 Consultez le tableau suivant pour les limites pour les valeurs de paramètre :  
  
|Paramètre|Limites|  
|---------------|------------|  
|`nHour`|0 - 23|  
|`nMin`|0 - 59|  
|`nSec`|0 - 59|  
  
 Si l’heure spécifiée par les paramètres de valeur n’est pas valide, l’état de cet objet a la valeur non valide et la valeur de cet objet n’est pas modifiée.  
  
 Voici quelques exemples de valeurs d’heure :  
  
|`nHour`|`nMin`|`nSec`|Valeur|  
|-------------|------------|------------|-----------|  
|1|3|3|01:03:03|  
|23|45|0|23:45:00|  
|25|30|0|Non valide|  
|9|60|0|Non valide|  
  
 Pour définir la date et heure, consultez [COleDateTime::SetDateTime](#setdatetime).  
  
 Pour plus d’informations sur les fonctions membres qui interrogent la valeur de cet `COleDateTime` d’objets, consultez les fonctions membres suivantes :  
  
- [GetDay](#getday)  
  
- [Méthode GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Pour plus d’informations sur les limites de `COleDateTime` valeurs, consultez l’article [Date et heure : prise en charge Automation](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [SetDate](#setdate).  
  
## <a name="see-also"></a>Voir aussi  
 [COleVariant, classe](../../mfc/reference/colevariant-class.md)   
 [Classe CTime](../../atl-mfc-shared/reference/ctime-class.md)   
 [Classe CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)




