# Regular Expression Examples:  
###### Find and Replace All Ignoring Case:
public String changeHamletToLeon(String stringToParse) {
        String regex = "(?i)hamlet";
        Pattern pattern = Pattern.compile(regex);
        Matcher m = pattern.matcher(stringToParse);
        String newSentence = m.replaceAll("Leon");

        return newSentence;