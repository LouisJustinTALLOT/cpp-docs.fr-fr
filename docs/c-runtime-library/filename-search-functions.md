---
title: Fonctions de recherche de nom de fichier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 777ac61828abbdc93bdf3fe6ceda05f927472494
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391800"
---
# <a name="filename-search-functions"></a>Fonctions de recherche de nom de fichier
Ces fonctions recherchent des noms de fichiers spécifiés et arrêtent ces recherches :  
  
-   [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)  
  
-   [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)  
  
-   [_findclose](../c-runtime-library/reference/findclose.md)  
  
## <a name="remarks"></a>Notes  
 La fonction `_findfirst` fournit des informations sur la première instance d’un nom de fichier correspondant au fichier spécifié dans l’argument `filespec` . Vous pouvez utiliser dans `filespec` n’importe quelle combinaison de caractères génériques prise en charge par le système d’exploitation hôte.  
  
 Les fonctions retournent des informations sur les fichiers dans une structure `_finddata_t`, définie dans IO.h. Les diverses fonctions de la famille utilisent de nombreuses variations sur la structure `_finddata_t` . La structure de base `_finddata_t` inclut les éléments suivants :  
  
 `unsigned attrib`  
 Attribut de fichier.  
  
 `time_t time_create`  
 Heure de la création du fichier (-1L pour les systèmes de fichiers FAT). Cette heure est stockée au format UTC. Pour la conversion en heure locale, utilisez [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).  
  
 `time_t time_access`  
 Heure du dernier accès au fichier (-1L pour les systèmes de fichiers FAT). Cette heure est stockée au format UTC. Pour la conversion en heure locale, utilisez `localtime_s`.  
  
 `time_t time_write`  
 Heure de la dernière opération d’écriture dans le fichier. Cette heure est stockée au format UTC. Pour la conversion en heure locale, utilisez `localtime_s`.  
  
 `_fsize_t size`  
 Longueur du fichier en octets.  
  
 `char name`[ `_MAX_PATH`]  
 Nom se terminant par un caractère Null d’un fichier ou d’un répertoire correspondant, sans le chemin.  
  
 Dans les systèmes de fichiers qui ne prennent pas en charge les heures de création ni de dernier accès pour un fichier, tels que le système FAT, les champs `time_create` et `time_access` ont toujours la valeur -1L.  
  
 `_MAX_PATH` est défini dans Stdlib.h avec une valeur de 260 octets.  
  
 Vous ne pouvez pas spécifier d’attributs cibles (comme `_A_RDONLY`) pour limiter l’opération de recherche. Ces attributs sont retournés dans le champ `attrib` de la structure `_finddata_t` et peuvent prendre les valeurs suivantes (définies dans IO.h). Les utilisateurs ne doivent pas compter sur le fait que ce sont les seules valeurs possibles pour le champ `attrib` .  
  
 `_A_ARCH`  
 Archive. Défini chaque fois que le fichier est modifié et supprimé par la commande **BACKUP** . Valeur : 0x20.  
  
 `_A_HIDDEN`  
 Fichier caché. Ne s’affiche généralement pas avec la commande DIR, sauf si vous utilisez l’option **/AH** . Retourne des informations sur les fichiers normaux et les fichiers qui ont cet attribut. Valeur : 0x02.  
  
 `_A_NORMAL`  
 Normal. Aucun autre attribut n’est défini pour le fichier et il est possible d’y effectuer des opérations de lecture ou d’écriture sans restriction. Valeur : 0x00.  
  
 `_A_RDONLY`  
 Lecture seule. Impossible d’ouvrir le fichier pour des opérations d’écriture ni de créer un fichier portant le même nom. Valeur : 0x01.  
  
 `_A_SUBDIR`  
 Sous-répertoire. Valeur : 0x10.  
  
 `_A_SYSTEM`  
 Fichier système. Ne s’affiche généralement pas avec la commande **DIR** , sauf si vous utilisez l’option **/A** ou **/A:S** . Valeur : 0x04.  
  
 `_findnext` recherche le nom suivant, le cas échéant, correspondant à l’argument `filespec` spécifié dans un appel antérieur à `_findfirst`. L’argument `fileinfo` doit pointer vers une structure initialisée par l’appel précédent à `_findfirst`. Si une correspondance est trouvée, le contenu de la structure `fileinfo` est modifié comme décrit précédemment. Dans le cas contraire, il reste inchangé. `_findclose` ferme le handle de recherche spécifié et libère toutes les ressources associées à la fois pour `_findfirst` et `_findnext`. Le handle retourné par `_findfirst` ou `_findnext` doit tout d’abord être transmis à `_findclose`, avant de pouvoir effectuer une opération de modification, telle que la suppression, sur les répertoires qui constituent les chemins transmis.  
  
 Vous pouvez imbriquer les fonctions `_find` . Par exemple, si un appel à `_findfirst` ou `_findnext` trouve le fichier qui est un sous-répertoire, une nouvelle recherche peut être lancée avec un autre appel à `_findfirst` ou `_findnext`.  
  
 `_wfindfirst` et `_wfindnext` sont des versions à caractères larges de `_findfirst` et `_findnext`. L’argument de structure des versions à caractères larges a le type de données `_wfinddata_t` , qui est défini dans IO.h et dans Wchar.h. Les champs de ce type de données sont les mêmes que ceux du type de données `_finddata_t` , sauf que dans `_wfinddata_t` , le champ de nom est de type `wchar_t` et non `char`. Sinon, `_wfindfirst` et `_wfindnext` se comportent de la même façon que `_findfirst` et `_findnext`.  
  
 `_findfirst` et `_findnext` utilisent le type de temps 64 bits. Si vous devez utiliser l’ancien type de temps 32 bits, vous pouvez définir `_USE_32BIT_TIME_T`. Les versions de ces fonctions qui ont le suffixe `32` dans leur nom utilisent le type de temps 32 bits et celles avec le suffixe `64` utilisent le type de temps 64 bits.  
  
 Les fonctions `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`et `_wfindnext32i64` se comportent également de la même façon que les versions de type de temps 32 bits de ces fonctions, mais elles utilisent et retournent des longueurs de fichiers 64 bits. Les fonctions `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`et `_wfindnext64i32` utilisent le type de temps 64 bits, mais des longueurs de fichiers 32 bits. Ces fonctions utilisent des variations appropriées du type `_finddata_t` où les champs ont des types différents pour l’heure et la taille du fichier.  
  
 `_finddata_t` est en fait une macro qui correspond à `_finddata64i32_t` (ou `_finddata32_t` si `_USE_32BIT_TIME_T` est défini). Le tableau suivant récapitule les différentes variations de `_finddata_t`:  
  
|Structure|Type de temps|Type de taille du fichier|  
|---------------|---------------|--------------------|  
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|  
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|  
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|  
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|  
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|  
  
 `_fsize_t` est un `typedef` pour `unsigned long` (32 bits).  
  
## <a name="example"></a>Exemple  
  
```  
// crt_find.c  
// This program uses the 32-bit _find functions to print  
// a list of all files (and their attributes) with a .C extension  
// in the current directory.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _finddata_t c_file;  
   intptr_t hFile;  
  
   // Find first .c file in current directory   
   if( (hFile = _findfirst( "*.c", &c_file )) == -1L )  
      printf( "No *.c files in current directory!\n" );  
   else  
   {  
      printf( "Listing of .c files\n\n" );  
      printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' );  
      printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' );  
      do {  
         char buffer[30];  
         printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " );  
         ctime_s( buffer, _countof(buffer), &c_file.time_write );  
         printf( " %-12s %.24s  %9ld\n",  
            c_file.name, buffer, c_file.size );  
      } while( _findnext( hFile, &c_file ) == 0 );  
      _findclose( hFile );  
   }  
}  
```  
  
```Output  
Listing of .c files  
  
RDO HID SYS ARC  FILE         DATE                           SIZE  
--- --- --- ---  ----         ----                           ----  
 N   N   N   Y   blah.c       Wed Feb 13 09:21:42 2002       1715  
 N   N   N   Y   test.c       Wed Feb 06 14:30:44 2002        312  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Appels système](../c-runtime-library/system-calls.md)