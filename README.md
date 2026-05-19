<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Apply Filter to Selected Layers - Manual</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            line-height: 1.6;
        }
        h1 {
            color: #2c3e50;
            border-bottom: 2px solid #3498db;
            padding-bottom: 10px;
        }
        h2 {
            color: #34495e;
            margin-top: 30px;
        }
        .step {
            background: #ecf0f1;
            padding: 15px;
            margin: 10px 0;
            border-left: 4px solid #3498db;
        }
        .warning {
            background: #fff3cd;
            padding: 15px;
            margin: 10px 0;
            border-left: 4px solid #ffc107;
        }
        .note {
            background: #d1ecf1;
            padding: 15px;
            margin: 10px 0;
            border-left: 4px solid #17a2b8;
        }
        code {
            background: #f8f9fa;
            padding: 2px 6px;
            border-radius: 3px;
            font-family: 'Courier New', monospace;
        }
        ul {
            margin-left: 20px;
        }
    </style>
</head>
<body>
    <h1>Apply Filter to Selected Layers</h1>
    
    <p>This script applies a filter layer to multiple paint layers individually while preserving their properties like blend mode, opacity, and <strong>Inherit Alpha</strong>.</p>

    <h2>How to Use</h2>
    
    <div class="step">
        <strong>Step 1:</strong> Create or select ONE filter layer (e.g., HSV Adjustment, Blur, Color Adjustment, etc.)
    </div>
    
    <div class="step">
        <strong>Step 2:</strong> Hold <code>Ctrl</code> (or <code>Cmd</code> on Mac) and select all the paint layers you want to apply the filter to
    </div>
    
    <div class="step">
        <strong>Step 3:</strong> Go to <code>Tools → Scripts → Apply Filter to Selected Layers</code>
    </div>
    
    <div class="step">
        <strong>Step 4:</strong> Wait for the script to process. Check the <strong>Scripter</strong> output for progress
    </div>

    <h2>What Gets Preserved</h2>
    <ul>
        <li><strong>Blend Mode</strong> - The layer's blending mode stays the same</li>
        <li><strong>Opacity</strong> - The layer's opacity percentage is preserved</li>
        <li><strong>Inherit Alpha</strong> - Alpha inheritance setting is maintained</li>
        <li><strong>Lock State</strong> - Locked layers will be locked again after processing</li>
        <li><strong>Layer Names</strong> - Original names are kept</li>
    </ul>

    <h2>How It Works</h2>
    <p>For each selected paint layer, the script:</p>
    <ol>
        <li>Temporarily disables Inherit Alpha (if enabled)</li>
        <li>Creates an isolated group containing the layer and filter</li>
        <li>Flattens the group to bake the filter effect</li>
        <li>Restores all original properties including Inherit Alpha</li>
    </ol>

    <div class="note">
        <strong>Note:</strong> The filter layer itself is NOT modified. It's only duplicated and applied to each target layer.
    </div>

    <h2>Requirements</h2>
    <ul>
        <li>Select <strong>exactly ONE</strong> filter layer</li>
        <li>Select <strong>one or more</strong> paint layers</li>
        <li>Layers must have a parent node (not root)</li>
    </ul>

    <div class="warning">
        <strong>Warning:</strong> This operation cannot be undone easily. Consider duplicating your layers or saving your document before running the script.
    </div>

    <h2>Troubleshooting</h2>
    
    <h3>Error: "No active document found"</h3>
    <p>Make sure you have a document open in Krita.</p>

    <h3>Error: "Select exactly ONE Filter Layer"</h3>
    <p>You either didn't select a filter layer, or you selected multiple filter layers. Only select one.</p>

    <h3>Error: "No valid target paint layers selected"</h3>
    <p>Make sure you've selected at least one paint layer along with the filter layer.</p>

    <h3>Layers appear blank after processing</h3>
    <p>This shouldn't happen with the current version. If it does, check the Scripter console for error messages and ensure your layers have actual pixel data.</p>

    <h2>Example Workflow</h2>
    <div class="step">
        <strong>Scenario:</strong> You have 10 character layers and want to apply the same color adjustment to all of them while keeping their Inherit Alpha settings.
        <ol>
            <li>Create an Adjustment filter layer</li>
            <li>Adjust the filter settings as desired</li>
            <li>Select the filter layer</li>
            <li>Hold Ctrl and click each of your layers</li>
            <li>Run the script: <code>Tools → Scripts → Apply Filter to Selected Layers</code></li>
            <li>All layers will have the filter baked in with properties preserved!</li>
        </ol>
    </div>

    <h2>Tips</h2>
    <ul>
        <li>The script processes layers in reverse order (bottom to top) to maintain stack integrity</li>
        <li>Check the Scripter console for detailed progress information</li>
    </ul>

</body>
</html>
