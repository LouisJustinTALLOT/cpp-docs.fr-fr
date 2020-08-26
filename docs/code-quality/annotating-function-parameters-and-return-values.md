---
title: Annotation des paramètres de fonction et des valeurs de retour
description: Guide de référence du paramètre de fonction et des annotations de valeur de retour.
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: b1831a2a504bb12473f564cd914340bc429fab8d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836672"
---
# <a name="annotating-function-parameters-and-return-values"></a>Annotation des paramètres de fonction et des valeurs de retour

Cet article décrit les utilisations typiques des annotations pour les paramètres de fonction simples (scalaires et pointeurs vers les structures et les classes) et la plupart des types de mémoires tampons. Cet article présente également les modèles d’utilisation courants pour les annotations. Pour les annotations supplémentaires liées aux fonctions, consultez [annotation du comportement](../code-quality/annotating-function-behavior.md)de la fonction.

## <a name="pointer-parameters"></a>Paramètres du pointeur

Pour les annotations dans le tableau suivant, lorsqu’un paramètre de pointeur est annoté, l’analyseur signale une erreur si le pointeur est null. Cette annotation s’applique aux pointeurs et à tout élément de données vers lequel pointe.

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_In_`

     Annote des paramètres d’entrée qui sont des valeurs scalaires, des structures, des pointeurs vers des structures et autres. Peut être utilisé explicitement sur des scalaires simples. Le paramètre doit être valide dans un état antérieur et ne sera pas modifié.

- `_Out_`

     Annote les paramètres de sortie qui sont des scalaires, des structures, des pointeurs vers des structures et autres. N’appliquez pas cette annotation à un objet qui ne peut pas retourner de valeur (par exemple, un scalaire passé par valeur). Le paramètre ne doit pas nécessairement être valide dans un état antérieur, mais doit être valide dans le billet.

- `_Inout_`

     Annote un paramètre qui sera modifié par la fonction. Elle doit être valide à la fois à l’état antérieur et postérieur, mais elle est supposée avoir des valeurs différentes avant et après l’appel. Doit s’appliquer à une valeur modifiable.

- `_In_z_`

     Pointeur vers une chaîne terminée par le caractère null qui est utilisée comme entrée. La chaîne doit être valide dans un état antérieur. Les variantes de `PSTR` qui possèdent déjà les annotations correctes sont préférées.

- `_Inout_z_`

     Pointeur vers un tableau de caractères se terminant par un caractère null qui sera modifié. Il doit être valide avant et après l’appel, mais il est supposé que la valeur a changé. La marque de fin null peut être déplacée, mais seuls les éléments jusqu’à la marque de fin null d’origine sont accessibles.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Pointeur vers un tableau, qui est lu par la fonction. Le tableau est de taille `s` et tous les éléments doivent tous être valides.

     La `_bytes_` variante donne la taille en octets au lieu des éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments. Par exemple, **`char`** les chaînes utilisent la `_bytes_` variante uniquement si une fonction similaire utilise **`wchar_t`** .

- `_In_reads_z_(s)`

     Pointeur vers un tableau qui se termine par un caractère null et a une taille connue. Les éléments jusqu’au terminateur null, ou `s` s’il n’existe pas de marque de fin null, doivent être valides dans un état antérieur. Si la taille est connue en octets, mettez `s` à l’échelle selon la taille de l’élément.

- `_In_reads_or_z_(s)`

     Pointeur vers un tableau qui se termine par un caractère null ou qui a une taille connue, ou les deux. Les éléments jusqu’au terminateur null, ou `s` s’il n’existe pas de marque de fin null, doivent être valides dans un état antérieur. Si la taille est connue en octets, mettez `s` à l’échelle selon la taille de l’élément. (Utilisé pour la `strn` famille.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Pointeur vers un tableau d' `s` éléments (REEE. bytes) qui sera écrit par la fonction. Les éléments de tableau ne doivent pas nécessairement être valides dans un état antérieur, et le nombre d’éléments valides dans le billet n’est pas spécifié. S’il existe des annotations sur le type de paramètre, elles sont appliquées dans un État postérieur. Par exemple, prenons le code suivant.

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     Dans cet exemple, l’appelant fournit une mémoire tampon d' `size` éléments pour `p1` . `MyStringCopy` rend certains de ces éléments valides. Plus important encore, l' `_Null_terminated_` annotation sur `PWSTR` signifie que `p1` se termine par un caractère NULL dans un État postérieur. De cette façon, le nombre d’éléments valides est toujours bien défini, mais un nombre d’éléments spécifique n’est pas requis.

     La `_bytes_` variante donne la taille en octets au lieu des éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments. Par exemple, **`char`** les chaînes utilisent la `_bytes_` variante uniquement si une fonction similaire utilise **`wchar_t`** .

- `_Out_writes_z_(s)`

     Pointeur vers un tableau d' `s` éléments. Les éléments ne doivent pas nécessairement être valides dans un état antérieur. Dans un État postérieur, les éléments au-dessus de la marque de fin null (qui doit être présent) doivent être valides. Si la taille est connue en octets, mettez `s` à l’échelle selon la taille de l’élément.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Pointeur vers un tableau, qui est à la fois lu et écrit dans la fonction. Il s’agit d' `s` éléments de taille et valides dans un état antérieur et postérieur.

     La `_bytes_` variante donne la taille en octets au lieu des éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments. Par exemple, **`char`** les chaînes utilisent la `_bytes_` variante uniquement si une fonction similaire utilise **`wchar_t`** .

- `_Inout_updates_z_(s)`

     Pointeur vers un tableau qui se termine par null et a une taille connue. Les éléments jusqu’au terminateur null (qui doit être présent) doivent être valides à la fois dans l’état antérieur et après l’État. La valeur de l’État postérieur est supposée être différente de la valeur de l’état antérieur ; qui comprend l’emplacement de la marque de fin null. Si la taille est connue en octets, mettez `s` à l’échelle selon la taille de l’élément.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Pointeur vers un tableau d' `s` éléments. Les éléments ne doivent pas nécessairement être valides dans un état antérieur. Dans un État postérieur, les éléments jusqu’au `c` -ième élément doivent être valides. La `_bytes_` variante peut être utilisée si la taille est connue en octets plutôt qu’en nombre d’éléments.

     Par exemple :

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Pointeur vers un tableau, qui est lu et écrit par la fonction. Il s’agit d' `s` éléments de taille, qui doivent tous être valides dans un état antérieur, et les `c` éléments doivent être valides dans un État postérieur.

     La `_bytes_` variante donne la taille en octets au lieu des éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments. Par exemple, **`char`** les chaînes utilisent la `_bytes_` variante uniquement si une fonction similaire utilise **`wchar_t`** .

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Pointeur vers un tableau, qui est lu et écrit par la fonction des éléments de taille `s` . Défini comme équivalent à :

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     En d’autres termes, tous les éléments qui existent dans la mémoire tampon jusqu’à `s` dans le préétat sont valides à l’état antérieur et postérieur.

     La `_bytes_` variante donne la taille en octets au lieu des éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments. Par exemple, **`char`** les chaînes utilisent la `_bytes_` variante uniquement si une fonction similaire utilise **`wchar_t`** .

- `_In_reads_to_ptr_(p)`

     Pointeur vers un tableau pour lequel `p - _Curr_` (autrement dit, `p` moins `_Curr_` ) est une expression valide. Les éléments antérieurs à `p` doivent être valides dans un état antérieur.

    Par exemple :

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Pointeur vers un tableau terminé par le caractère null pour lequel l’expression `p - _Curr_` (autrement dit, `p` moins `_Curr_` ) est une expression valide. Les éléments antérieurs à `p` doivent être valides dans un état antérieur.

- `_Out_writes_to_ptr_(p)`

     Pointeur vers un tableau pour lequel `p - _Curr_` (autrement dit, `p` moins `_Curr_` ) est une expression valide. Les éléments before `p` ne doivent pas nécessairement être valides dans un état antérieur et doivent être valides dans un État postérieur.

- `_Out_writes_to_ptr_z_(p)`

     Pointeur vers un tableau se terminant par un caractère null pour lequel `p - _Curr_` (autrement dit, `p` MINUS `_Curr_` ) est une expression valide. Les éléments before `p` ne doivent pas nécessairement être valides dans un état antérieur et doivent être valides dans un État postérieur.

## <a name="optional-pointer-parameters"></a>Paramètres de pointeur facultatifs

Quand une annotation de paramètre de pointeur comprend `_opt_` , elle indique que le paramètre peut être null. Dans le cas contraire, l’annotation se comporte comme la version qui n’inclut pas `_opt_` . Voici une liste des `_opt_` variantes des annotations de paramètre de pointeur :

:::row:::
   :::column:::
      `_In_opt_`\
      `_Out_opt_`\
      `_Inout_opt_`\
      `_In_opt_z_`\
      `_Inout_opt_z_`\
      `_In_reads_opt_`\
      `_In_reads_bytes_opt_`\
      `_In_reads_opt_z_`
   :::column-end:::
   :::column:::
      `_Out_writes_opt_`\
      `_Out_writes_opt_z_`\
      `_Inout_updates_opt_`\
      `_Inout_updates_bytes_opt_`\
      `_Inout_updates_opt_z_`\
      `_Out_writes_to_opt_`\
      `_Out_writes_bytes_to_opt_`\
      `_Out_writes_all_opt_`\
      `_Out_writes_bytes_all_opt_`
   :::column-end:::
   :::column:::
      `_Inout_updates_to_opt_`\
      `_Inout_updates_bytes_to_opt_`\
      `_Inout_updates_all_opt_`\
      `_Inout_updates_bytes_all_opt_`\
      `_In_reads_to_ptr_opt_`\
      `_In_reads_to_ptr_opt_z_`\
      `_Out_writes_to_ptr_opt_`\
      `_Out_writes_to_ptr_opt_z_`
   :::column-end:::
:::row-end:::

## <a name="output-pointer-parameters"></a>Paramètres du pointeur de sortie

Les paramètres de pointeur de sortie nécessitent une notation spéciale pour lever l’ambiguïté sur la valeur NULL sur le paramètre et l’emplacement pointé.

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_Outptr_`

   Le paramètre ne peut pas être null et, dans l’État postérieur, l’emplacement pointé ne peut pas être null et doit être valide.

- `_Outptr_opt_`

   Le paramètre peut avoir la valeur null, mais dans l’État postérieur, l’emplacement pointé ne peut pas être null et doit être valide.

- `_Outptr_result_maybenull_`

   Le paramètre ne peut pas avoir la valeur null et, dans l’État postérieur, l’emplacement pointé peut avoir la valeur null.

- `_Outptr_opt_result_maybenull_`

   Le paramètre peut avoir la valeur null et, dans l’État postérieur, l’emplacement pointé peut avoir la valeur null.

  Dans le tableau suivant, des sous-chaînes supplémentaires sont insérées dans le nom de l’annotation pour qualifier davantage la signification de l’annotation. Les différentes sous-chaînes sont `_z` , `_COM_` , `_buffer_` , `_bytebuffer_` et `_to_` .

> [!IMPORTANT]
> Si l’interface que vous annotez est COM, utilisez la forme COM de ces annotations. N’utilisez pas les annotations COM avec une autre interface de type.

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   Le pointeur retourné a l' `_Null_terminated_` annotation.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Le pointeur retourné a une sémantique COM, ce qui explique pourquoi il contient une `_On_failure_` condition de publication indiquant que le pointeur retourné a la valeur null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Le pointeur retourné pointe vers une mémoire tampon valide d' `s` éléments de taille ou d’octets.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Le pointeur retourné pointe vers une mémoire tampon d' `s` éléments ou d’octets de taille, dont le premier `c` est valide.

Certaines conventions d’interface présument que les paramètres de sortie sont annulés en cas d’échec. À l’exception du code COM explicite, les formulaires répertoriés dans le tableau suivant sont préférés. Pour le code COM, utilisez les formulaires COM correspondants répertoriés dans la section précédente.

- `_Result_nullonfailure_`

   Modifie d’autres annotations. Le résultat est défini sur null si la fonction échoue.

- `_Result_zeroonfailure_`

   Modifie d’autres annotations. Le résultat est défini sur zéro si la fonction échoue.

- `_Outptr_result_nullonfailure_`

   Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est destinée à un paramètre non facultatif.

- `_Outptr_opt_result_nullonfailure_`

   Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est destinée à un paramètre facultatif.

- `_Outref_result_nullonfailure_`

   Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est destinée à un paramètre de référence.

## <a name="output-reference-parameters"></a>Paramètres de référence de sortie

Le paramètre de référence est couramment utilisé pour les paramètres de sortie. Pour les paramètres de référence de sortie simples tels que `int&` , `_Out_` fournit la sémantique correcte. Toutefois, lorsque la valeur de sortie est un pointeur tel que `int *&` , les annotations de pointeur équivalentes comme `_Outptr_ int **` ne fournissent pas la sémantique correcte. Pour exprimer de façon concise la sémantique des paramètres de référence de sortie pour les types pointeur, utilisez les annotations composites suivantes :

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_Outref_`

     Le résultat doit être valide dans postérieur à l’État et ne peut pas être null.

- `_Outref_result_maybenull_`

     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur.

- `_Outref_result_buffer_(s)`

     Le résultat doit être valide dans postérieur à l’État et ne peut pas être null. Pointe vers une mémoire tampon valide d’éléments de taille `s` .

- `_Outref_result_bytebuffer_(s)`

     Le résultat doit être valide dans postérieur à l’État et ne peut pas être null. Pointe vers une mémoire tampon valide de taille `s` octets.

- `_Outref_result_buffer_to_(s, c)`

     Le résultat doit être valide dans postérieur à l’État et ne peut pas être null. Pointe vers la mémoire tampon d' `s` éléments dont le premier `c` est valide.

- `_Outref_result_bytebuffer_to_(s, c)`

     Le résultat doit être valide dans postérieur à l’État et ne peut pas être null. Pointe vers la mémoire tampon d' `s` octets dont le premier `c` est valide.

- `_Outref_result_buffer_all_(s)`

     Le résultat doit être valide dans postérieur à l’État et ne peut pas être null. Pointe vers une mémoire tampon valide d' `s` éléments valides de taille.

- `_Outref_result_bytebuffer_all_(s)`

     Le résultat doit être valide dans postérieur à l’État et ne peut pas être null. Pointe vers une mémoire tampon valide d' `s` octets d’éléments valides.

- `_Outref_result_buffer_maybenull_(s)`

     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur. Pointe vers une mémoire tampon valide d’éléments de taille `s` .

- `_Outref_result_bytebuffer_maybenull_(s)`

     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur. Pointe vers une mémoire tampon valide de taille `s` octets.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur. Pointe vers la mémoire tampon d' `s` éléments dont le premier `c` est valide.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans l’état de publication. Pointe vers la mémoire tampon d' `s` octets dont le premier `c` est valide.

- `_Outref_result_buffer_all_maybenull_(s)`

     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans l’état de publication. Pointe vers une mémoire tampon valide d' `s` éléments valides de taille.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans l’état de publication. Pointe vers une mémoire tampon valide d' `s` octets d’éléments valides.

## <a name="return-values"></a>Valeurs retournées

La valeur de retour d’une fonction ressemble à un `_Out_` paramètre mais se trouve à un niveau de déréférencement différent, et vous n’avez pas à considérer le concept du pointeur sur le résultat. Pour les annotations suivantes, la valeur de retour est l’objet annoté (un scalaire, un pointeur vers un struct ou un pointeur vers une mémoire tampon). Ces annotations ont la même sémantique que l' `_Out_` annotation correspondante.

:::row:::
   :::column:::
      `_Ret_z_`\
      `_Ret_writes_(s)`\
      `_Ret_writes_bytes_(s)`\
      `_Ret_writes_z_(s)`\
      `_Ret_writes_to_(s,c)`\
      `_Ret_writes_maybenull_(s)`\
      `_Ret_writes_to_maybenull_(s)`\
      `_Ret_writes_maybenull_z_(s)`
   :::column-end:::
   :::column:::
      `_Ret_maybenull_`\
      `_Ret_maybenull_z_`\
      `_Ret_null_`\
      `_Ret_notnull_`\
      `_Ret_writes_bytes_to_`\
      `_Ret_writes_bytes_maybenull_`\
      `_Ret_writes_bytes_to_maybenull_`
   :::column-end:::
:::row-end:::

## <a name="format-string-parameters"></a>Paramètres de chaîne de format

- `_Printf_format_string_` Indique que le paramètre est une chaîne de format à utiliser dans une `printf` expression.

     **Exemple**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_` Indique que le paramètre est une chaîne de format à utiliser dans une `scanf` expression.

     **Exemple**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_` Indique que le paramètre est une chaîne de format à utiliser dans une `scanf_s` expression.

     **Exemple**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Autres annotations courantes

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Le paramètre, le champ ou le résultat se trouve dans la plage (inclusive) de `low` à `hi` . Équivalent à `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` qui est appliqué à l’objet annoté avec les conditions préalables ou postérieures à l’État appropriées.

    > [!IMPORTANT]
    > Bien que les noms contiennent « in » et « out », la sémantique de `_In_` et `_Out_` ne s’applique **pas** à ces annotations.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     La valeur annotée est exactement `expr` . Équivalent à `_Satisfies_(_Curr_ == expr)` qui est appliqué à l’objet annoté avec les conditions préalables ou postérieures à l’État appropriées.

- `_Struct_size_bytes_(size)`

     S’applique à une déclaration de classe ou de struct. Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, avec le nombre d’octets spécifié par `size` . Par exemple :

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     La taille de la mémoire tampon en octets d’un paramètre `pM` de type `MyStruct *` est ensuite considérée comme :

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="see-also"></a>Voir aussi

- [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Présentation de SAL](../code-quality/understanding-sal.md)
- [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)
- [Annotations des structs et des classes](../code-quality/annotating-structs-and-classes.md)
- [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)
- [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)
- [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
