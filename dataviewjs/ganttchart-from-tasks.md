# Gantt chat view of Tasks

## Important points to remember
1. Not all tasks need to go in ganttcharts: only place long terms tasks here.
2. To mark a task for gantt chart, put hashtag #ganttchart on it and ensure start and due date is marked that will plot the entry based on priority.


```dataviewjs
// Priority mapping based on emojis
const priorityMap = {
    "🔺": "Highest",
    "⏫": "High",
    "⏺️": "Medium",
    "🔽": "Low",
    "⏬": "Lowest"
};

// Function to determine priority based on emoji in task text
const getPriority = (text) => {
    for (let emoji in priorityMap) {
        if (text.includes(emoji)) {
            return priorityMap[emoji];
        }
    }
    return "Medium"; // Default to Medium if no emoji is found
};

const today = new Date(); // Get the current date
const todayStr = today.toISOString().split("T")[0]; // YYYY-MM-DD format
const tasks = dv.pages("").file.tasks.where(t => t.text.includes("#ganttchart") && t.start && t.due && !t.completed );

if (tasks.length > 0) {
    let ganttData = `
\`\`\`mermaid

gantt
    title Tasks with Start and Due Dates
    dateFormat YYYY-MM-DD
    axisFormat %d-%b
    `;
    
    // Group tasks by priority and create a critical group
    const priorityGroups = {"Critical": [], "Highest": [], "High": [], "Medium": [], "Low": [], "Lowest": [] };
    tasks.forEach(task => {
        const dueDate = new Date(task.due.toString().split("T")[0]); // Extract due date as Date object
        const isCritical = dueDate < today; // Check if the task is overdue

        const priority = isCritical ? "Critical" : getPriority(task.text);

        let sanitizedTaskText = task.text
            .replace(/#[\w-]+/g, "") // Remove hashtags
            .replace(/(?:\p{Emoji_Presentation}|[\u2600-\u27BF])\s*\d{4}-\d{2}-\d{2}/gu, "") // Remove dates with emojis
            .replace(/[\n\r]+/g, " ") // Remove newlines
            .trim(); // Trim leading/trailing spaces

        for (let emoji in priorityMap) { 
            sanitizedTaskText = sanitizedTaskText.replace(emoji, "").trim(); 
        }

        const startDate = task.start.toString().split("T")[0]; // Extract YYYY-MM-DD
        const endDate = task.due.toString().split("T")[0]; // Extract YYYY-MM-DD
        
        if (sanitizedTaskText) { // Ensure non-empty text
			if (isCritical) {
				priorityGroups[priority].push(`    ${sanitizedTaskText} overdue :crit, ${startDate}, ${todayStr}`);
			} else { 
			    priorityGroups[priority].push(`    ${sanitizedTaskText} :active, ${startDate}, ${endDate}`);
	        }
        }
    });

    // Add tasks to Gantt chart by priority
    for (const priority in priorityGroups) {
        if (priorityGroups[priority].length > 0) {
            ganttData += `\nsection ${priority}\n`;
            ganttData += priorityGroups[priority].join("\n");
        }
    }

    ganttData += `\n\`\`\``;

    // Debug mode: Show raw text
    dv.el("pre", ganttData); 
} else {
    dv.paragraph("No tasks found with Gantt chart marker and with start and due dates. Mark text with #ganttchart and ensure both start and due dates are marked.");
}

```






