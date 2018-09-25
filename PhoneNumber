// cmatsunaga17@georgefox.edu
// Program 2
// 2018-09-13


/**
 * This is a PhoneNumber class that represents only basic, 10-digit
 * telephone numbers based on the North American Numbering Plan. This
 * class implements a Comparable<T> interface, in which the T object is
 * a PhoneNumber. The interface enables lexical (numerical) sorting
 * by area code, prefix, then line number.
 * 
 * A basic phone number will consist of 3 parts (10 digits in all)
 * - an area code: first 3 digits, allows [2-9][0-9][0-9]
 * - a prefix: middle 3 digits, allows [2-9][0-9][0-9]
 * - a line number: last 4 digits, allows [0–9][0–9][0–9][0–9]
 * 
 * In this class, country codes will not be included. Only numbers
 * (0-9) must be used to represent any part of the phone number, no
 * letters should be used.
 * 
 * @author cmatsunaga17@georgefox.edu
 */
public class PhoneNumber implements Comparable<PhoneNumber>
{
   // used in isValidPhoneNumber() method
   private static final String VALID_AREA_CODE = "[2-9][0-9][0-9]";
   private static final String VALID_PREFIX = "[2-9][0-9][0-9]";
   private static final String VALID_LINE_NUMBER = "[0-9][0-9][0-9][0-9]";

   // used in parsePhoneNumber() method
   private static final int AREA_CODE_PORTION = 0;
   private static final int PREFIX_PORTION = 1;
   private static final int LINE_NUMBER_PORTION = 2;

   private String _areaCode;
   private String _prefix;
   private String _lineNumber;

   /**
    * Constructs a new PhoneNumber with Strings representing parts of
    * a whole phone number: area code, prefix, and line number. Uses
    * the isValidPhoneNumber method to test to see if the parameters
    * are valid. If not valid, then the constructor throws an
    * IllegalArgumentException.
    * 
    * @param areaCode The area code (first 3 numbers)
    * @param prefix The prefix (middle 3 numbers)
    * @param lineNumber The line number (last 4 numbers)
    * @throws IllegalArgumentException Throws exception if any part of
    *         the phone number is not valid
    */
   public PhoneNumber(String areaCode, String prefix, String lineNumber)
   {
      _areaCode = areaCode;
      _prefix = prefix;
      _lineNumber = lineNumber;

      if (!isValidPhoneNumber(areaCode, prefix, lineNumber))
      {
         throw new IllegalArgumentException("Invalid. "
               + "Read the javadocs...");
      }
   }

   /**
    * Returns the area code of the phone number.
    * 
    * @return The area code (first 3 numbers)
    */
   public String getAreaCode()
   {
      return _areaCode;
   }

   /**
    * Returns the prefix of the phone number.
    * 
    * @return The prefix (middle 3 numbers)
    */
   public String getPrefix()
   {
      return _prefix;
   }

   /**
    * Returns the line number of the phone number.
    * 
    * @return The line number (last 4 numbers)
    */
   public String getLineNumber()
   {
      return _lineNumber;
   }

   /**
    * Returns the whole phone number by combining the area code, prefix,
    * and line number. The String includes just the digits in the phone
    * number, with no symbols or extra characters (no delimiters).
    * 
    * @return A String of the phone number (10 numbers in all)
    */
   public String getDigits()
   {
      return _areaCode + _prefix + _lineNumber;
   }

   /**
    * Returns the whole phone number by combining the area code, prefix,
    * and line number. The String returned has been formatted with
    * dashes "-" between the parts.
    * 
    * @return A String of the phone number (10 numbers with 2 dashes)
    */
   public String toString()
   {
      return _areaCode + "-" + _prefix + "-" + _lineNumber;
   }

   /**
    * Compares two phone numbers lexicographically. Both phone numbers
    * being compared must have 10 digits.
    * 
    * If:
    * - both Strings are equal, returns int 0
    * - first String is lexicographically greater than the second
    *   String, returns int 1 (positive value)
    * - second String is lexicographically greater than the first
    *   String, returns int -1 (negative value)
    * 
    * @return An integer 0, -1, or 1
    */
   public int compareTo(PhoneNumber o)
   {
      return getDigits().compareTo(o.getDigits());
   }

   /**
    * Checks to make sure the phone number is valid. Using the Strings
    * .match() method, each digit in the phone number is checked to see
    * if it lies in the boundaries provided. In the process, length of
    * each part of the phone number is also checked. A basic, North
    * American phone number should follow the pattern 3-3-4. Also,
    * symbols like dashes or parentheses should not be used (the phone
    * number will not be valid).
    * 
    * A phone number is valid if:
    * - area code has 3 numbers & first number is not 0 or 1
    * - prefix has 3 numbers & first number is not 0 or 1
    * - line number has 4 numbers (all digits in any place allowed)
    * If any of these conditions are not true, the phone number is not
    * valid.
    * 
    * @param areaCode The area code (first 3 numbers)
    * @param prefix The prefix (middle 3 numbers)
    * @param lineNumber The line number (last 4 numbers)
    * @return A boolean - true if phone number is valid
    *                     false if phone number is invalid
    */
   public static boolean isValidPhoneNumber(String areaCode,
                         String prefix, String lineNumber)
   {
      boolean result = false;
      if (areaCode == null || prefix == null || lineNumber == null)
      {
         result = false;
      }
      else if (areaCode.matches(VALID_AREA_CODE)
            && prefix.matches(VALID_PREFIX)
            && lineNumber.matches(VALID_LINE_NUMBER))
      {
         result = true;
      }
      return result;
   }

   /**
    * Parses (analyzes) through the phone number.This method should
    * expect the String passed in to have dashes (ex: 808-469-2711).
    * 
    * The phone number passed into the method gets separated into parts
    * and assigned to area code (first part, index 0), prefix (second
    * part, index 1), and line number (last part, index 2). If the
    * phone number parameter is not valid, the IllegalArgumentException
    * will be thrown.
    * 
    * @param phoneNumber The phone number (10 numbers with dashes "-")
    * @return A new instance of PhoneNumber (if valid)
    * @throws IllegalArgumentException Throws exception if any part of
    *         the phone number is not valid
    */
   public static PhoneNumber parsePhoneNumber(String phoneNumber)
   {
      PhoneNumber p1 = null;
      if (phoneNumber != null)
      {
         String[] parsedNumber = phoneNumber.split("-");
         if (parsedNumber.length != 3)
         {
            throw new IllegalArgumentException();
         }
         // see above comment, not a magic number!
         String areaCode = parsedNumber[AREA_CODE_PORTION];
         String prefix = parsedNumber[PREFIX_PORTION];
         String lineNumber = parsedNumber[LINE_NUMBER_PORTION];

         p1 = new PhoneNumber(areaCode, prefix, lineNumber);
      }
      else
      {
         throw new IllegalArgumentException();
      }
      return p1;
      // can't assume that every phone number passed in will be formatted
      // the way I think (2 dashes)
      // if 2 dashes not brought in, indexes would all be off
   }
}
