-LIBRARY ieee;
USE ieee.std_logic_1164.ALL;
USE ieee.std_logic_1164.ALL;

ENTITY memory controller IS
    PORT (
        RAM_ADDR : IN std_logic_vector(6 downto 0);
        RAM_DATA_IN : IN std_logic_vector(7 downto 0);
        RAM_WR : IN std_logic;
        RAM_CLOCK : IN std_logic;
        RAM_DATA_OUT : OUT std_logic_vector(7 downto 0)
    );
END Single_Port_RAM;

ARCHITECTURE behavior OF Single_Port_RAM IS
    TYPE RAM_ARRAY IS ARRAY (0 TO 127) OF std_logic_vector(7 downto 0);
    SIGNAL RAM : RAM_ARRAY := (others => (others => '0'));
BEGIN
    PROCESS(RAM_CLOCK)
    BEGIN
        IF rising_edge(RAM_CLOCK) THEN
            IF RAM_WR = '1' THEN
                RAM(CONV_INTEGER(RAM_ADDR)) <= RAM_DATA_IN;
            END IF;
            RAM_DATA_OUT <= RAM(CONV_INTEGER(RAM_ADDR));
        END IF;
    END PROCESS;
END behaviour;

<!---
Govindusujitha/Govindusujitha is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
