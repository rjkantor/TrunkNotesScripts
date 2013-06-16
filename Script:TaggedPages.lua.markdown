Title: Script:TaggedPages.lua
Timestamp: 2013-06-16 09:37:42 +0000
Created: 2013-06-16 08:59:31 +0000
Last Accessed: 2013-06-16 09:37:42 +0000
Times Accessed: 10
Tags: Lua, Script, CoreMeta
Metadata: 

--
-- Displays all  pages that do have tags
-- Author: RJKantor
--

function string.starts(String,Start)
   return string.sub(String,1,string.len(Start))==Start
end


returnValue = ""

for pageIteration, currentPageTitle in ipairs(wiki.titles()) do
	
	if (string.starts(currentPageTitle,"Docs:") == false and string.starts(currentPageTitle, "Special:") == false) then
	
		currentPageTags = wiki.get(currentPageTitle).tags

		if (#currentPageTags > 0) then
                returnValue = returnValue .." [[" .. currentPageTitle .. "]] ………. "
                for i, tag in ipairs(wiki.get(currentPageTitle).tags) do
                  returnValue = returnValue .. "[[" .. tag .. "]] "
                end
                  returnValue = returnValue .. "\n"
             end
	end
end

return returnValue
