---
title: Les fonctions CRT non prises en charge dans les applications de plateforme Windows universelle | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed8b5c150632d035060b0e34f3962f2e903990a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle
Plusieurs fonctions CRT (C runtime) ne sont pas disponibles quand vous créez des applications pour la plateforme Windows universelle (UWP). Dans certains cas, les solutions de contournement sont disponibles :-par exemple, vous pouvez utiliser des API Win32 ou Windows Runtime. Toutefois, dans d’autres cas, les fonctions CRT sont exclues, car les fonctionnalités qui leur correspondent ou les API de prise en charge ne sont pas applicables aux applications UWP. Pour rechercher une autre méthode qui est pris en charge pour le Windows Runtime, consultez [Alternatives aux API Windows dans les applications UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
Le tableau suivant répertorie les fonctions CRT qui ne sont pas disponibles quand vous créez des applications UWP, et indique les éventuelles solutions de contournement applicables.  
  
## <a name="unsupported-crt-functions"></a>Fonctions CRT non prises en charge  
  
||||  
|-|-|-|  
|_beep _sleep _seterrormode|Ces fonctions sont obsolètes dans les versions précédentes de CRT. En outre, les API Win32 correspondantes ne sont pas disponibles pour les applications UWP.|Aucune solution de contournement.|  
|chdir _chdrive getcwd|Ces fonctions sont obsolètes ou ne sont pas thread-safe.|Utilisez _chdir, _getcwd et les fonctions connexes.|  
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|Ces fonctions sont utilisées pour lire et écrire directement dans la console. Les applications UWP ne fonctionnent qu’avec les GUI. Elles ne prennent pas de console en charge.|Aucune solution de contournement.|  
|getpid|Cette fonction est obsolète.|Utilisez _getpid ou l’API Win32 `GetCurrentProcessId()`.|  
|_getdiskfree|Non disponible.|Utilisez l’API Win32 `GetDiskFreeSpaceExW()`.|  
|_getdrive _getdrives|L’API correspondante n’est pas disponible pour les applications UWP.|Aucune solution de contournement.|  
|_inp _inpd _inpw _outp _outpd _outpw inp inpd inpw outp outpd outpw|E/S de port non pris en charge dans les applications UWP.|Aucune solution de contournement.|  
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset_l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|Les chaînes multioctets ne sont pas prises en charge dans les applications UWP.|Utilisez des chaînes Unicode à la place.|  
|_pclose _pipe _popen _wpopen|La fonctionnalité pipe n’est pas disponible pour les applications UWP.|Aucune solution de contournement.|  
|_resetstkoflw|Les API Win32 de prise en charge ne sont pas disponibles pour les applications UWP.|Aucune solution de contournement.|  
|_getsystime _setsystime|Il s’agit d’API obsolètes dans les versions précédentes de CRT. En outre, un utilisateur ne peut pas définir l’heure système dans une application UWP en raison d’un manque d’autorisations.|Pour obtenir uniquement l’heure système, utilisez l’API Win32 `GetSystemTime`. Impossible de définir l’heure système.|  
|_environ _putenv _putenv_s _searchenv _searchenv_s _dupenv_s _wputenv _wputenv_s _wsearchenv getenv getenv_s putenv _wdupenv_s _wenviron _wgetenv _wgetenv_s _wsearchenv_s tzset|Les variables d’environnement ne sont pas disponibles pour les applications UWP.|Aucune solution de contournement. Pour définir le fuseau horaire, utilisez _tzset.|  
|_loaddll _getdllprocaddr _unloaddll|Il s’agit de fonctions obsolètes dans les versions précédentes de CRT. En outre, l’utilisateur ne peut pas charger les DLL, à l’exception de celles figurant dans le même package d’application.|Utilisez les API Win32 `LoadPackagedLibrary`, `GetProcAddress`et `FreeLibrary` pour charger et utiliser les DLL packagées.|  
|_wexecl _wexecle _wexeclp _wexeclpe _wexecv _wexecve _wexecvp _wexecvpe _execl _execle _execlp _execlpe _execv _execve _execvp _execvpe _spawnl _spawnle _spawnlp _spawnlpe _spawnv _spawnve _spawnvp _spawnvpe _wspawnl _wspawnle _wspawnlp _wspawnlpe _wspawnv _wspawnve _wspawnvp _wspawnvpe _wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|La fonctionnalité n’est pas disponible dans les applications UWP. Une application UWP ne peut pas appeler une autre application UWP ou une application de bureau.|Aucune solution de contournement.|  
|_heapwalk _heapadd _heapchk _heapset _heapused|Ces fonctions sont généralement utilisées avec le tas. Toutefois, les API Win32 correspondantes ne sont pas prises en charge dans les applications UWP. De plus, les applications ne peuvent plus créer ou utiliser les tas privés.|Aucune solution de contournement. Toutefois, `_heapwalk` est disponible dans DEBUG CRT, à des fins de débogage uniquement. Ils ne peut pas être utilisés dans les applications qui sont téléchargées au Microsoft Store.|  
  
 Les fonctions suivantes sont disponibles dans la bibliothèque CRT pour les applications UWP, mais doit être utilisées uniquement lorsque le Win32 correspondante ou APIs Windows Runtime ne peut pas être utilisés, par exemple, lorsque vous déplacez des bases de code volumineuses  
  
|||  
|-|-|  
|Fonctions de chaîne simple octet : par exemple, `strcat`, `strcpy`, `strlwr`, et ainsi de suite.|Vos applications UWP strictement Unicode, car toutes les API Win32 et APIs Windows Runtime qui sont exposées utilisent Unicode uniquement de jeux de caractères.  Les fonctions simple octet sont réservées au portage de bases de code volumineuses ou doivent être évitées. Les fonctions wide char correspondantes doivent être utilisées à la place quand cela est possible.|  
|Fonctions d’E/S de flux ou d’E/S de fichier de bas niveau, par exemple, `fopen`, `open`et ainsi de suite.|Ces fonctions sont synchrones, ce qui n’est pas recommandé pour les applications UWP. Dans vos applications UWP, utilisez des API asynchrones pour ouvrir, lire et écrire dans des fichiers afin d’éviter le verrouillage du thread d’interface utilisateur. Ces API sont, par exemple, celles de la classe `Windows::Storage::FileIO` .|  
  
## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Applications du Windows 8.x Store et applications Windows Phone 8.x  
 Outre les API mentionnées précédemment, les API suivantes ne sont pas disponibles dans les applications du Windows 8.x Store et les applications Windows Phone 8.x.  
  
||||  
|-|-|-|  
|_beginthread _beginthreadex _endthread _endthreadex|Les API Win32 de thread ne sont pas disponibles dans les applications du Windows 8.x Store.|Utilisez `Windows Runtime Windows::System::Threading::ThreadPool` ou `concurrency::task` à la place.|  
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|Le concept d’un répertoire de travail ne s’applique pas aux applications du Windows 8.x Store.|Utilisez plutôt des chemins complets.|  
|_getpid|Cette fonction est obsolète dans les versions précédentes de CRT.|Utilisez l’API Win32 `GetCurrentProcessId()`|  
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ismbblead_l _ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Les chaînes multioctets ne sont pas prises en charge dans les applications du Windows 8.x Store.|Utilisez des chaînes Unicode à la place.|  
|_tzset|Les variables d’environnement ne sont pas disponibles pour les applications du Windows 8.x Store.|Aucune solution de contournement.|  
|_get_heap_handle, _heapmin|Les API Win32 correspondantes ne sont pas prises en charge dans les applications du Windows 8.x Store. De plus, les applications ne peuvent plus créer de tas privé.|Aucune solution de contournement. Toutefois, `_get_heap_handle` est disponible dans DEBUG CRT, à des fins de débogage uniquement.|